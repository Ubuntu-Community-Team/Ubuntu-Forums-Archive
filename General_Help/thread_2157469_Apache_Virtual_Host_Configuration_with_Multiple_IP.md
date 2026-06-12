---
title: "Apache Virtual Host Configuration with Multiple IPs"
date: 2013-06-25
forum: General Help
---

### Post by fbm on 2013-06-25
Hi,

I'm trying to configure an Ubuntu server with 4 Public IPs to display "This is a shared IP site" if any of the IPs are accessed directly. The server has IP-based virtual-hosts configured on the different IPs. So far, I'm not having any success with it. The virtual hosts work fine, but I wan't anyone accessing any IP directly to get the shared IP site message.

Any help will be appreciated.

Ubuntu version:
[FONT=Courier New][SIZE=3]root@goku:/etc/apache2# cat /etc/*-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.2 LTS"
NAME="Ubuntu"
VERSION="12.04.2 LTS, Precise Pangolin"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu precise (12.04.2 LTS)"
VERSION_ID="12.04"
root@goku:/etc/apache2#
[/SIZE][/FONT]
Francis

---

### Post by SeijiSensei on 2013-06-25
If you have separate IP-based virtual hosts each with its own DocumentRoot, you need to put the same index.html in each one of them, or use symlinks to a common file.

---

