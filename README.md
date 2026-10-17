# Design tokens demo

A working example of [figma-live-tokens](https://github.com/tirthkparikh/figma-live-tokens) as a GitHub Action.

**Live page:** https://tirthkparikh.github.io/design-tokens-demo/

| Workflow | What it does |
| --- | --- |
| [Figma sync](.github/workflows/figma-sync.yml) | Pulls the public *IBM Design Language* colour styles from Figma, builds CSS / Tailwind v4 / JS into `tokens/figma/dist`, and opens a pull request listing every changed variable. Runs weekly and on demand. |
| [Tokens Studio build](.github/workflows/tokens-studio.yml) | When `tokens/studio/tokens.json` changes (as pushed by the Tokens Studio plugin), builds CSS with a light and a dark theme and opens a pull request. |
| [Pages](.github/workflows/pages.yml) | Publishes the palette page after each merge. |

## Use it in your repo

1. Create a Figma personal access token with read access to file content (Figma → Settings → Security).
2. Add it as a repository secret named `FIGMA_TOKEN`.
3. In **Settings → Actions → General**, tick **Allow GitHub Actions to create and approve pull requests**.
4. Copy [`.github/workflows/figma-sync.yml`](.github/workflows/figma-sync.yml) and change `figma-file` to your file.

Figma limits how often its API can be read on some seat types, so poll weekly or trigger the workflow by hand when the design changes.
