---
title: "aptURL issue"
date: 2017-04-16
forum: General Help
---

### Post by techsupport-hotmail on 2017-04-16
hi. im trying to install flash but when i click download on the flash site for ubuntu, a box appears and asks what aptURL to use. i got no idea what it means as i assumed it downloaded automatically.

---

### Post by wildmanne39 on 2017-04-16
The Google Chrome browser is shipped with Flash bundled, and does not need a plug-in.

To install for firefox do:
```
sudo apt install flashplugin-installer
```
Thanks

---

### Post by howefield on 2017-04-16
> **wildmanne39 said:**
> The Google Chrome browser is shipped with Flash bundled, and does not need a plug-in.

I don't think that is the case any more but could be wrong :)

..trying to install from zesty..

```
sudo apt install -s ~/Downloads/Linux_Packages/google-chrome-stable_current_amd64.deb 
[sudo] password for hugh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'google-chrome-stable' instead of '/home/hugh/Downloads/Linux_Packages/google-chrome-stable_current_amd64.deb'
The following additional packages will be installed:
  libpango1.0-0 libpangox-1.0-0
The following NEW packages will be installed
  google-chrome-stable libpango1.0-0 libpangox-1.0-0
0 to upgrade, 3 to newly install, 0 to remove and 0 not to upgrade.
Inst libpangox-1.0-0 (0.0.2-5 Ubuntu:17.04/zesty [amd64])
Inst libpango1.0-0 (1.40.4-1 Ubuntu:17.04/zesty [amd64])
Inst google-chrome-stable (57.0.2987.133-1 local-deb [amd64])
Conf libpangox-1.0-0 (0.0.2-5 Ubuntu:17.04/zesty [amd64])
Conf libpango1.0-0 (1.40.4-1 Ubuntu:17.04/zesty [amd64])
Conf google-chrome-stable (57.0.2987.133-1 local-deb [amd64])
```

and dependencies being..

```
Depends: gconf-service, libasound2 (>= 1.0.16), libatk1.0-0 (>= 1.12.4), libc6 (>= 2.11), libcairo2 (>= 1.2.4), libcups2 (>= 1.4.0), libdbus-1-3 (>= 1.1.4), libexpat1 (>= 2.0.1), libfontconfig1 (>= 2.9.0), libfreetype6 (>= 2.3.9), libgcc1 (>= 1:4.1.1), libgconf-2-4 (>= 2.31.1), libgdk-pixbuf2.0-0 (>= 2.22.0), libglib2.0-0 (>= 2.26.0), libgtk2.0-0 (>= 2.24.0), libnspr4 (>= 2:4.9-2~) | libnspr4-0d (>= 1.8.0.10) | libnspr4 (>= 4.9.5-0ubuntu0), libnss3 (>= 2:3.13.4-2~) | libnss3-1d (>= 3.12.4), libpango1.0-0 (>= 1.14.0), libstdc++6 (>= 4.8.0), libx11-6 (>= 2:1.4.99.1), libx11-xcb1, libxcb1 (>= 1.6), libxcomposite1 (>= 1:0.3-1), libxcursor1 (>> 1.1.2), libxdamage1 (>= 1:1.1), libxext6, libxfixes3, libxi6 (>= 2:1.2.99.4), libxrandr2 (>= 2:1.2.99.3), libxrender1, libxss1, libxtst6, ca-certificates, fonts-liberation, libappindicator1, libnss3 (>= 3.17.2), lsb-base (>= 4.1), xdg-utils (>= 1.0.2), wget
```

For Chrome(ium) based browsers I'd suggest adobe-flashplugin from the Partners repository which will also take care of Firefox.

---

### Post by wildmanne39 on 2017-04-16
Thanks howefield.:)

---

