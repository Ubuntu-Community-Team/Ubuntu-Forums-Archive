---
title: "Openoffice and flashplayer have messed up colors"
date: 2004-11-08
forum: General Help
---

### Post by ubuntu_demon on 2004-11-08
Hi,

My problem is that the colors of openoffice and flashplayer are so crappy that the apps aren't usable. So I think it's the same problem.

I'm using vncserver on my ubuntu system because I got a crappy videocard and no space for an extra monitor. 

from vnc.conf :

$depth = "32";
$pixelformat = "rgb565";

The only non-warty packages are :
I installed flashplayer from deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat)
I installed GAIM,amsn and firefox from hoary.

thnx,

---

### Post by ubuntu_demon on 2004-11-08
(i'm using windows XP and and vncviewer from realvnc)

solution vnc.conf :
$pixelformat = "rgb888"

---

