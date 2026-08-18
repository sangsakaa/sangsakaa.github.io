readme = """# Romantic Landing Page ❤️

Landing page romantis untuk GitHub Pages.

## Cara pakai

1. Buat repository GitHub bernama `sangsakaa.github.io`.
2. Upload `index.html` ke branch `main`.
3. Buka **Settings → Pages**.
4. Pada **Build and deployment**, pilih source yang sesuai (misalnya GitHub Actions atau branch `main`).
5. Situs akan tersedia di `https://sangsakaa.github.io/`.

Semua tampilan utama ada di satu file `index.html`, jadi mudah diedit.
"""

(root / "index.html").write_text(index_html, encoding="utf-8")
(root / "README.md").write_text(readme, encoding="utf-8")

zip_path = Path("/mnt/data/romantic-github-pages-sangsakaa.zip")
with zipfile.ZipFile(zip_path, "w", zipfile.ZIP_DEFLATED) as z:
    for file in root.iterdir():
        z.write(file, file.name)

print(f"File siap: {zip_path}")
