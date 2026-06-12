---
title: "Evolution email couldn't open link with browser"
date: 2018-01-18
forum: General Help
---

### Post by fely35 on 2018-01-18
To open web links with Evolution on Kubuntu 17.10 I had to download and run this:

sudo gio mime x-scheme-handler/http
sudo gio mime x-scheme-handler/https

results in this output (twice):

Default application for “x-scheme-handler/http”: firefox.desktop
Registered applications:
        firefox.desktop
        chromium-browser.desktop
Recommended applications:
        firefox.desktop
        chromium-browser.desktop

---

