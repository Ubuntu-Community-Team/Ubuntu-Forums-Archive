---
title: "Remove and reinstall chromium"
date: 2023-06-20
forum: General Help
---

### Post by bjngchn on 2023-06-20
Most sites not working because of cloud flare fascism.  Need to reinstall chromium.  I uninstall chromium and reinstall it. What, chromium with  the same version (same settings) is back, which means, it was not removed. Need two command  lines to totally REMOVE and then totally "re"INSTALL chromium.   I hate chromium, but it is the only one that will work for some sites. kubuntu 14+

---

### Post by #&amp;thj^% on 2023-06-20
I hope I'm not caught up in your mini rant, but I assume you mean:
```
sudo apt autoremove --purge  chromium.
```
If it's a Snap then I'm no help.

---

### Post by bjngchn on 2023-06-20
Ok, tried: ...  sudo apt autoremove --purge  chromium  .....  and here is the response of the terminal: ..   E: Command line option --purge is not understood

---

### Post by #&amp;thj^% on 2023-06-20
What Version Ubuntu are you running?
```
apt policy chromium
chromium:
  Installed: 114.0.5735.133-1
  Candidate: 114.0.5735.133-1
  Version table:
 *** 114.0.5735.133-1 500
        500 https://deb.kaisenlinux.org kaisen-rolling/main amd64 Packages
        100 /var/lib/dpkg/status
     113.0.5672.126-1 500
        500 https://deb.debian.org/debian bookworm/main amd64 Packages

```
For the uninstall:
```
sudo apt autoremove --purge chromium
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages will be REMOVED:
  avahi-utils* chromium* chromium-common* chromium-sandbox* cups-pk-helper*
  gir1.2-handy-1* gir1.2-packagekitglib-1.0* gir1.2-polkit-1.0*
  graphicsmagick* libgraphicsmagick-q16-3* libre2-10* libu2f-udev*
  python3-cupshelpers* python3-smbc* system-config-printer*
  system-config-printer-common* system-config-printer-udev*
0 upgraded, 0 newly installed, 17 to remove and 1 not upgraded.
After this operation, 257 MB disk space will be freed.
Do you want to continue? [Y/n] 


```
Just if you need to reference any of the removed packages:
```
&#9492;&#9472;> apt depends chromium
chromium
  Depends: libasound2 (>= 1.0.17)
  Depends: libatk-bridge2.0-0 (>= 2.5.3)
  Depends: libatk1.0-0 (>= 2.2.0)
  Depends: libatomic1 (>= 4.8)
  Depends: libatspi2.0-0 (>= 2.9.90)
  Depends: libbrotli1 (>= 0.6.0)
  Depends: libc6 (>= 2.35)
  Depends: libcairo2 (>= 1.6.0)
  Depends: libcups2 (>= 1.7.0)
  Depends: libdbus-1-3 (>= 1.9.14)
  Depends: libdouble-conversion3 (>= 2.0.0)
  Depends: libdrm2 (>= 2.4.75)
  Depends: libevent-2.1-7 (>= 2.1.8-stable)
  Depends: libexpat1 (>= 2.0.1)
  Depends: libflac12 (>= 1.3.0)
  Depends: libfontconfig1 (>= 2.12.6)
  Depends: libfreetype6 (>= 2.11.1)
  Depends: libgbm1 (>= 17.1.0~rc2)
  Depends: libgcc-s1 (>= 4.0)
  Depends: libglib2.0-0 (>= 2.39.4)
  Depends: libjpeg62-turbo (>= 1:1.5.0)
  Depends: libjsoncpp25 (>= 1.9.5)
  Depends: liblcms2-2 (>= 2.2+git20110628)
  Depends: libminizip1 (>= 1.1)
  Depends: libnspr4 (>= 2:4.9-2~)
  Depends: libnss3 (>= 2:3.31)
  Depends: libopenh264-7 (>= 2.3.1+dfsg)
  Depends: libopenjp2-7 (>= 2.2.0)
  Depends: libopus0 (>= 1.1)
  Depends: libpango-1.0-0 (>= 1.14.0)
  Depends: libpng16-16 (>= 1.6.2-1)
  Depends: libpulse0 (>= 0.99.1)
  Depends: libre2-10 (>= 20201101+dfsg)
  Depends: libsnappy1v5 (>= 1.1.9)
  Depends: libstdc++6 (>= 12)
  Depends: libwebp7 (>= 1.2.4)
  Depends: libwebpdemux2 (>= 1.2.4)
  Depends: libwebpmux3 (>= 1.2.4)
  Depends: libwoff1 (>= 1.0.0)
  Depends: libx11-6
  Depends: libxcb1 (>= 1.9.2)
  Depends: libxcomposite1 (>= 1:0.4.5)
  Depends: libxdamage1 (>= 1:1.1)
  Depends: libxext6
  Depends: libxfixes3
  Depends: libxkbcommon0 (>= 0.5.0)
  Depends: libxml2 (>= 2.7.4)
  Depends: libxnvctrl0
  Depends: libxrandr2
  Depends: libxslt1.1 (>= 1.1.27)
  Depends: zlib1g (>= 1:1.2.2)
 |Depends: libgtk-3-0
  Depends: <xdg-desktop-portal-backend>
    xdg-desktop-portal-gnome
    xdg-desktop-portal-gtk
    xdg-desktop-portal-kde
    xdg-desktop-portal-wlr
  Depends: chromium-common (= 114.0.5735.133-1)
  Conflicts: <libgl1-mesa-swx11>
  Conflicts: <libnettle4>
  Conflicts: libsecret-1-0 (<< 0.18)
  Breaks: chromium-lwn4chrome (<= 1.0-2)
  Breaks: chromium-tt-rss-notifier (<= 0.5.2-2)
  Recommends: chromium-sandbox
  Suggests: chromium-l10n
  Suggests: chromium-shell
  Suggests: chromium-driver

```
And if you do a turn around re-install then clean "Apt cache"
```
sudo apt clean
```
Now you can re-install if desired.

---

### Post by bjngchn on 2023-06-20
14.04  Commands above don't work.  Other commands I found on internet "worked", but didn't change the chromium or its settings after uninstalling/purging, and (re-) installing. I uninstall it, it goes away (chromium icon doesn't work).  I reinstall,..previous one together with its bookmarks, and settings come back. So nothing happens, when something should have happened.

---

### Post by #&amp;thj^% on 2023-06-20
Yep 14.04 Commands above don't work.
This is UN-suppoted done dead kaput.
Sorry i can't in good faith support a security risk. (Nothing Personal)

---

