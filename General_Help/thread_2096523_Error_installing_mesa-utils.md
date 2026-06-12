---
title: "Error installing mesa-utils"
date: 2012-12-20
forum: General Help
---

### Post by philled on 2012-12-20
I'm trying to run xbmc on my 12.04 Ubuntu machine. I've got xbmc installed but there's a mesa-utils package missing which seems to be needed and which won't install.

[FONT=Courier New]Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise/universe mesa-utils amd64 8.0.1+git20110129+d8f7d6b-0ubuntu2
  403  Forbidden
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/m/mesa-demos/mesa-utils_8.0.1+git20110129+d8f7d6b-0ubuntu2_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/m/mesa-demos/mesa-utils_8.0.1+git20110129+d8f7d6b-0ubuntu2_amd64.deb)  403  Forbidden[/FONT]

Any idea how I can get this package to install?

---

### Post by philled on 2012-12-20
Actually, I've solved this. I think the Austrralian mirror is missing  the package so I changed /etc/apt/sources.list so it doesn't use the  Aussie mirror:

[FONT=Courier New]## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
###deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise universe
###deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise universe
###deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-updates universe
###deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-updates universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates universe[/FONT]

---

