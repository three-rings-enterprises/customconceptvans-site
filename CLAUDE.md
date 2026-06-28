# Custom Concept Vans — Static Site Archive

## What this is
A static site archive of customconceptvans.com, scraped with HTTrack on 2026-06-28 and hosted on GitHub Pages. The shop is no longer operational; this is a preservation site.

## Hosting
- **GitHub repo:** https://github.com/three-rings-enterprises/customconceptvans-site
- **GitHub account:** `three-rings-enterprises`
- **Hosted via:** GitHub Pages, `main` branch, root `/`
- **Domain:** `customconceptvans.com` (registered on GoDaddy)
- **HTTPS:** Auto-provisioned via Let's Encrypt through GitHub Pages

## Directory structure
```
/
├── index.html               ← redirects to customconceptvans.com/index.html
├── CNAME                    ← "customconceptvans.com" — required for GitHub Pages custom domain
├── .nojekyll                ← prevents Jekyll processing (needed for %-encoded asset paths)
├── .gitignore               ← excludes httrack artifacts + third-party mirror domains
├── customconceptvans.com/   ← all HTML pages
├── img1.wsimg.com/          ← site images (~280MB, ~1200 files; GoDaddy's image CDN mirror)
└── isteam.wsimg.com/        ← additional image assets
```

**Important:** The `img1.wsimg.com/` and `isteam.wsimg.com/` folders must stay at the repo root. All HTML files reference images with relative paths like `../img1.wsimg.com/...` — moving them will break the site.

## DNS (GoDaddy)
4 × A records: `@` → GitHub Pages IPs (185.199.108-111.153)
1 × CNAME: `www` → `three-rings-enterprises.github.io`

## Pages
about, airliner-cabinetry, baja-cruiser, build-services, claim-jumper, claim-jumper-mtb, consultation, downloads, flarespace-installation, full-builds, gallery, heli-trailer, home-1, index, jobs, lightnin, mobile-tms-clinic, power-systems-gallery, solar-tax-credit, the-otter, the-shark-tank, tire-and-wheel-info, transit-crew-build, van-gogh, window-upgrade-process

## HTTrack scrape command
```bash
cd ~/Desktop/ccv-site-final
httrack "https://customconceptvans.com/" \
  -O "./customconceptvans" \
  "+customconceptvans.com/*.html" \
  "+customconceptvans.com/the-shark-tank*" \
  "+*.wsimg.com/*" \
  "-customconceptvans.com/m/*" \
  "-customconceptvans.com/store/*" \
  "-*/ols/*" "-*/cdn-cgi/*" "-*/cart/*" "-*/checkout/*" \
  "-*.facebook.com/*" "-*.instagram.com/*" "-*.youtube.com/*" \
  "-*.godaddy.com/*" "-*.fbcdn.net/*" "-*.cdninstagram.com/*" \
  "-*.yelp.com/*" "-*.google.com/*" "-*.googletagmanager.com/*" \
  "-*.w3.org/*" \
  --robots=0 --depth=3 --ext-depth=1 --disable-security-limits
```
