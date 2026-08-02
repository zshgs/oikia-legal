# Homie — public pages

The Privacy Policy, Terms of Service and Support page for the Homie iOS app,
hosted on GitHub Pages so App Store Connect has a reachable URL for each.

| Page | URL | Used for |
|---|---|---|
| `privacy.html` | https://zshgs.github.io/homieai-legal/privacy.html | App Store Connect **Privacy Policy URL** (required) |
| `support.html` | https://zshgs.github.io/homieai-legal/support.html | App Store Connect **Support URL** (required) |
| `terms.html` | https://zshgs.github.io/homieai-legal/terms.html | linked from the policy and from the app |
| `index.html` | https://zshgs.github.io/homieai-legal/ | landing page, so the root is not a 404 |

## Do not edit the HTML here

Every file in this repo is **build output**. The text lives in
`src/features/legal/content.ts` in the private `homieai` repo — the same module
the in-app Privacy and Terms screens render from, so the hosted pages and what a
reviewer sees inside the app cannot disagree.

Editing the HTML directly would break exactly that guarantee: the website would
say one thing and the app another, which is the kind of inconsistency App Review
looks for.

To change the text:

```bash
# in the homieai repo
$EDITOR src/features/legal/content.ts
npm run build:legal          # regenerates public/
cp public/*.html ../homieai-legal/
git -C ../homieai-legal commit -am "Update policies" && git -C ../homieai-legal push
```

The pages are self-contained — inlined CSS, no scripts, no network requests, and
they follow the reader's light/dark preference.
