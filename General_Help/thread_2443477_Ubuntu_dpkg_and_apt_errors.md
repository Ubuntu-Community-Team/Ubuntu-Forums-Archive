---
title: "Ubuntu dpkg and apt errors"
date: 2020-05-16
forum: General Help
---

### Post by resistance22 on 2020-05-16
[COLOR=#242729][FONT=Arial]So I updated to ubuntu 20.04 LTS and then I started getting this error on the top bar of my desktop:[/FONT][/COLOR]
[INDENT][FONT=inherit]**Error opening the cache(E:flAbspath on /var/lib/dpkg/status failed - realpath (13:permission denied), E: could not open file - open(2: No such file or directory), E: Problem opening,E: The Package list or status file could not be parsed or open). This usually means that your installed packages have unmet dependencies.**[/FONT]
[/INDENT][COLOR=#242729][FONT=Arial]Also when I use **sudo apt update** I get the warning:[/FONT][/COLOR]
[INDENT][FONT=inherit]**W: Download is performed unsandboxed as root as file '/var/lib/apt/lists/partial/mirror.de.leaseweb.net_ubuntu_dists_focal_InRelease' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)**[/FONT]
[/INDENT][COLOR=#242729][FONT=Arial]I checked my status file in /var/lib/dpkg/status and here is the file :[/FONT][/COLOR]
[INDENT][FONT=inherit]**-rw-r--r-- 1 root root 3192885 May 16 11:12 /var/lib/dpkg/status**[/FONT]
[/INDENT][COLOR=#242729][FONT=Arial]I also set changed the ownership of** /var/lib/apt/lists/partial/** to **_apt:root** but **nothing** seems to work![/FONT][/COLOR]

---

