---
title: "mplayer &amp; totem firefox"
date: 2007-01-30
forum: General Help
---

### Post by darweth on 2007-01-30
hey... i have always used mplayer for all embedded videos within firefox.  it is a wonderful piece of code!  i went on vacation for 12 days and came back to a Totem update.  This update pulverizes my mplayer settings and FORCES itself upon me.  I want my videos to play with mplayer, not totem!  I removed totem-mozilla and all was chippy, but that removal removes ubuntu-desktop.  i reinstalled ubuntu-desktop, but then totem-mozilla is automatically reinstalled!  uh!  i want ubuntu-desktop (for updates and all) but NOT totem-mozilla.  what can I do?

---

### Post by meng on 2007-01-30
Terminal:
cd /usr/lib/mozilla-firefox/plugins
sudo mkdir quarantine
sudo mv libtotem* quarantine

---

