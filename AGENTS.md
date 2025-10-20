# Repository Guidelines

## Project Structure & Module Organization
- Source: Jekyll site using al-folio (multilingual).
- Content: `_pages/<lang>/` (static pages), `_posts/<lang>/` (blog posts), `_projects/`, `_news/`.
- Presentation: `_layouts/`, `_includes/`, `_sass/`, `assets/` (img/css/js).
- Data & refs: `_data/` (YAML), `_bibliography/` (BibTeX), `_plugins/` (Ruby).
- Config: `_config.yml`, `Gemfile`, `package.json`.

## Build, Test, and Development Commands
- Install deps: `bundle install` (Ruby), `npm i` (Prettier/purgecss).
- Run locally: `bundle exec jekyll serve --livereload` → http://localhost:4000.
- Build site: `bundle exec jekyll build` → outputs to `_site/`.
- Purge CSS (after build): `npx purgecss -c purgecss.config.js`.
- Docker dev: `docker compose up` (no local Ruby needed).
- CI build helper: `bin/cibuild` (used by CI; safe for local checks).

## Coding Style & Naming Conventions
- Languages: Markdown + Liquid, HTML, SCSS, YAML.
- Formatting: Prettier with Liquid plugin (`.prettierrc`). Run `npx prettier -w .`.
- Indentation: 2 spaces; wrap at ~150 chars (see `printWidth`).
- Posts: `_posts/<lang>/YYYY-MM-DD-title.md` with front matter (`layout`, `title`, `lang`, `permalink`).
- Pages: `_pages/<lang>/<slug>.md`. Assets under `assets/` with logical subfolders.

## Testing Guidelines
- Primary check: site builds cleanly (no Liquid errors). Use `bin/cibuild`.
- Link and accessibility checks run in GitHub Actions (lychee, axe); review CI results on PRs.
- Optional local checks: run `bundle exec jekyll build` then open `_site/` in a browser.
- Use pre-commit hooks: `pre-commit install` (trailing spaces, EOF, YAML).

## Commit & Pull Request Guidelines
- Commits: concise, imperative summaries (e.g., "Add en-us project page").
- Scope changes by area (pages, posts, layout, assets). Reference issues (`Fixes #123`).
- Before PR: run local build, format with Prettier, include screenshots for visual changes.
- PRs: clear description, affected pages/paths, language coverage (update all relevant locales).

## Configuration Tips
- Set `url` and `baseurl` in `_config.yml` for correct links.
- Do not commit `_site/`. Deploy via Actions or `bin/deploy` to `gh-pages` if needed.
