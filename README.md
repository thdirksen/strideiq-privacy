# strideiq-privacy

The static privacy website for the StrideIQ Android app. It is plain HTML and CSS, with no JavaScript, cookies, analytics, web fonts or external requests.

- `index.html`: the landing page.
- `privacy/index.html`: the privacy policy.
- `styles.css`: shared styles. The colours come from the app's `src/styles.css`.
- `404.html`: the "page not found" page. Its links are absolute paths under `/strideiq-privacy/`.
- `support/`, `delete-data/`, `terms/`, `apps/`: "coming soon" placeholders. They are not linked yet.
- `.nojekyll`: serves the files as they are.

## Updating the policy
1. Edit `privacy/index.html`. Change **Last updated**, and keep **Effective date** unless you are publishing a new version.
2. Regenerate the plain-text copy: `python3 -c "import html,re;s=open('privacy/index.html').read();print(html.unescape(re.sub(r'<[^>]+>','',s)))" > POLICY-DRAFT.txt`.
3. Check that no `[DECISION NEEDED` marker remains: `grep -rn "DECISION NEEDED" --include=*.html .` should print nothing.
4. Commit and push. GitHub Pages serves the `main` branch root.

When you add a page, copy the header and footer of an existing page and link it from the nav or footer.
