# Weavz Local Computer Use

[![npm version](https://img.shields.io/npm/v/%40weavz-io%2Flocal-computer-use?label=npm)](https://www.npmjs.com/package/@weavz-io/local-computer-use)
[![npm downloads](https://img.shields.io/npm/dm/%40weavz-io%2Flocal-computer-use?label=downloads)](https://www.npmjs.com/package/@weavz-io/local-computer-use)
[![GitHub release](https://img.shields.io/github/v/release/weavz/weavz-local-computer-use?label=release)](https://github.com/weavz/weavz-local-computer-use/releases)
[![Release workflow](https://github.com/weavz/weavz-local-computer-use/actions/workflows/release.yml/badge.svg?branch=main)](https://github.com/weavz/weavz-local-computer-use/actions/workflows/release.yml)
[![License](https://img.shields.io/npm/l/%40weavz-io%2Flocal-computer-use?label=license)](https://github.com/weavz/weavz-local-computer-use/blob/main/LICENSE)

Launcher for [Weavz](https://weavz.io) Agent Local Computer Control.

This package validates a Weavz local computer session URL and opens the signed Weavz Local Computer
Control macOS app. The app owns macOS Screen Recording and Accessibility permissions, shows visible
control status, and connects outbound to the Weavz session.

Signed app download metadata is published in `app-manifest.json`. Native app source and signing
configuration are not part of this public package.

## Usage

Start a local computer session from Weavz first. The `start_session` or `ensure_connected` action
returns a `localRunnerCommand` that looks like this:

```bash
npx -y @weavz-io/local-computer-use connect --url "<localRunnerUrl from start_session>"
```

Run that command on the Mac that should host the session.

## Requirements

- Node.js 22.13+
- macOS with the signed Weavz Local Computer Control app installed
- A Weavz local computer session URL from `agent-local-computer-control`

## Security

Treat the `localRunnerCommand` as a short-lived secret. It contains a session-scoped credential and
should only be run by the user on the Mac that should attach to the session.

By default, the CLI only accepts Weavz hosted session URLs and loopback development URLs. For
self-hosted Weavz endpoints, pass `--allow-custom-url` only when you trust the endpoint:

```bash
npx -y @weavz-io/local-computer-use connect \
  --url "<self-hosted localRunnerUrl from start_session>" \
  --allow-custom-url
```

## Links

- [Weavz](https://weavz.io)
- [Documentation](https://weavz.io/docs/concepts/local-computer-control)
- [Dashboard](https://dashboard.weavz.io)
- [npm package](https://www.npmjs.com/package/@weavz-io/local-computer-use)
