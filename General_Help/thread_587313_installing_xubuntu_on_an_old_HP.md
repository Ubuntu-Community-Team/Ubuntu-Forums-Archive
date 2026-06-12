---
title: "installing xubuntu on an old HP"
date: 2007-10-22
forum: General Help
---

### Post by mactechy on 2007-10-22
Hey there
I have an Old  HP Omnibook xe2 and am trying to install xubuntu 7.10 with an alternate CD.
It goes fine until i get to mounting the CD, it cannot mount it for some weird reason.... any suggestions? Thanks!

---

### Post by kerry_s on 2007-10-22
> **mactechy said:**
> Hey there
I have an Old  HP Omnibook xe2 and am trying to install xubuntu 7.10 with an alternate CD.
It goes fine until i get to mounting the CD, it cannot mount it for some weird reason.... any suggestions? Thanks!

i use to have 1 of those, the cd drive sucked, it's very picky. the older distro's worked really well, mine use to run debian, than dsl in ram when the hd died. i always had problems with any ubuntu on it.
try debian instead-> 
[http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-xfce-CD-1.iso](http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-xfce-CD-1.iso)

if debian don't work, then try dsl->
[http://damnsmalllinux.org/](http://damnsmalllinux.org/)

---

### Post by mactechy on 2007-11-19
Sorry mate,
That did'nt work!

---

### Post by roberf1 on 2008-01-19
Folks I am hving an issue loading Ubuntu 7.1 onto and Omnibook from a cd (checks itself as OK) the cd loads fine to the original choice menu but from there any of the start or install menus give me a list of messages of which I can make no sense (I am a novice - actually if I could find a lower classification I would use it) The Omnibook is an XE2 cd version as noted by a older poster - additionally W2K is currently running on it but I have not gotten the w2k driver to update the system for screen size etc... to get ubuntu to load I have tried several modifications in the bios in terms of options but I am more or less shooting in the dark - I bought this computer specifically to load ubuntu onto so I could work my way up to novice user with an intent to switching several computers at my place of employment over to the Ubuntu system -  the computer I am writing this from is  a compaq Armada M700 which appears to have no problems with ubuntu but I am too chicken to install fully because this computer does not have a working mouse....
---- the messages all start like ----
[  195.840000] EIP is a tunion fs_rename+0x4df/ etc....
[   195.84000] eax: 0000800 etc...
etc
[   195.84000] process debconf-set-sel (pid:4998, ti=ca2aa2000 task=c78f4530 etc etc
etc
[  195.84000] Call Trace:
[  195.84000]  [<c0188cde>] vfs_rename - etc
[  195.84000]  [<c018afbf6>] sys_renameat+01 etc
anyhow hopefully this gives a clue?
Any help would be GREAT
Thanks
Floyd

---

### Post by louieb on 2008-01-19
Weird a PC that will boot from a CD but the program on the CD cant find the CD drive.  Most of the time the boot option **ide=nodma**  fixes the problem. 
[Cheat Codes - Knoppix Documentation Wiki]("http://www.knoppix.net/wiki/Cheat_Codes")
[BootOptions - Ubuntu Documentation]("https://help.ubuntu.com/community/BootOptions")

---

