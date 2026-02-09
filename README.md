# Website Update Guide

This guide explains the standard workflow for updating the website.

## What You Need

- A standard computer with Terminal (or Command Prompt).
- A code editor ([VS Code](https://code.visualstudio.com/) or similar).
- [Git](https://git-scm.com/) and [Hugo](https://gohugo.io/) installed.
- [GitHub Desktop](https://desktop.github.com/) (recommended).

## Where Things Live

- Main page content:
  - Bio text: `content/aboutme.md`
  - Working papers list: `content/working_papers.yaml`
  - Publications list: `content/publications.yaml`
  - Older papers list: `content/older_papers.yaml`
- PDFs and downloadable files: `static/`
  - Most paper files are in `static/pdf/`
  - Data/replication files are in `static/datacode/`
- Sidebar settings (site title, short bio, profile photo path): `config.toml`
- Page templates/layout logic: `layouts/`

Do not manually edit `public/` (it is generated automatically).

## Standard Workflow (Every Update)

1. Make your content/file edits.
2. Preview locally:
   - Open Terminal and navigate to the GitHub folder in your terminal: `/GitHub/sdellavi.github.io/`.
   - Run `hugo server`.
   - Open the provided localhost link in your browser.
   - Verify that the changes look correct.
3. Stop the preview server with `Control + C` in Terminal.
4. Open GitHub Desktop.
5. (Recommended) Review the changed files.
6. Write a clear commit message (example: `Add working paper on ...`).
7. Click **Commit to main**.
8. Click **Push origin**.

### How To Add a New Paper

1. Add the pdfs of the paper/appendix to `static/pdf/` (and add any relevant replication/code files to `static/datacode/`).
2. Open the correct YAML file:
   - `content/working_papers.yaml` for Working Papers
   - `content/publications.yaml` for Publications
   - `content/older_papers.yaml` for Older Papers
3. Add a new entry under `works:` using this format:

```yaml
works:
- title: "Paper title"
  pdflink: "/pdf/your-paper-file.pdf"
  coauthors: "Coauthor A and Coauthor B"
  book: "Journal/status line"
  note: "Optional short note"
  links:
  - url: "/pdf/appendix.pdf"
    text: "Online Appendix"
    note: "Optional note"
  abstract: >
    Abstract text.
```

4. Save the file.
5. Preview with `hugo serve`.
6. If everything looks correct, commit and push from GitHub Desktop.

### Other Common Edits

- Edit the bio section: update `content/aboutme.md`.
- Edit sidebar title/short bio/photo path: update `config.toml`.
- Edit an existing paper: modify the relevant YAML entry in `content/*.yaml`.
- Reorder papers: move entries up/down within the relevant `.yaml` files.
- Update page structure/styling: edit files in `layouts/` (only if needed, be careful if doing so).

## Quick Checklist Before Pushing

- Site preview looks correct with `hugo serve`.
- New PDF/data links open correctly.
- PDF links use `/pdf/...` and data links use `/datacode/...` where appropriate.
- No accidental changes to unrelated files.
