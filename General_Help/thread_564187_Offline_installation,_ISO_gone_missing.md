---
title: "Offline installation, ISO gone missing"
date: 2007-09-30
forum: General Help
---

### Post by dgcarter on 2007-09-30
I downloaded Wubi and the Ubuntu Studio ISO, put both in the same directory, did the installation and all had worked well... But now my ISO (all 867MB of it) has gone missing, I noticed that it disappeared while Wubi was installing ubuntu. Where can I find it, or how can I get it back?

---

### Post by ado_raul on 2007-10-01
u can get i back in 2 ways:

1. unintaling wubi u have an option to back-up /home and downloaded iso
2. try looking in the install dir  [drive]:\wubi\install\

nice day.

---

### Post by ago on 2007-10-01
> **dgcarter said:**
> I downloaded Wubi and the Ubuntu Studio ISO, put both in the same directory, did the installation and all had worked well... But now my ISO (all 867MB of it) has gone missing, I noticed that it disappeared while Wubi was installing ubuntu. Where can I find it, or how can I get it back?

The ISO gets moved from the original folder to C:\wubi\install
If you uninstall Wubi it gets moved to C:\wubi-backup

The reason it gets moved is that copying is slow and it wastes space

---

### Post by ntxploits on 2008-01-09
[IMG]http://picasaweb.google.com/ntxploits/Ubuntu/photo#5153672149266091202[/IMG]

i have the same problem... i put it in e:\ubuntu directory... unfortunately, i cannot find the iso files at all. it's lucky that i already backup it in another directory manually.. 

another problem is when it delete the iso file, then wubi trying to download the new iso from the internet...

your advice is highly appreciated

---

### Post by ntxploits on 2008-01-09
i just check my e: directory and found that wubi create another folder.. e:\wubi

i try to put iso files into E:\wubi\install directory manually, unfortunately, it keeps downloading the iso from the internet.

anything i can do to rectify this problem

i'm using Wubi-7.04.04.exe with ubuntu-7.04-alternate-i386.iso
before this, i already tried Wubi-7.10-alpha-rev386 with Ubuntu 7.10, unfortunately after the installation, nothing appear but error message

> BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in shell (ash)_
Enter 'help' for a list of builts-in commands

(initrams)

---

### Post by ago on 2008-01-10
Uninstall wubi and put the iso file in the same folder as the wubi executable. Note that 7.04 requires the ALTERNATE ISO while 7.10 requires the DESKTOP ISO. If you have the correct ISO but wubi still tries to download it might be that the ISO you have is corrupted (run a checksum).

---

### Post by ntxploits on 2008-01-10
thanks... yes, the iso image is correct. however, i never run the checksum for the iso file.
here is the result, and seems like it was different from the website that i refer below

> D:\ntxploits>md5sum.exe D:\Linux\ubuntu-7.04-alternate-i386.iso
\7983b6ce75d1afa5d5c83d93aeefe58c *D:\\ntxploits\\ubuntu-7.04-alternate-i386.iso

> ff0cc7c9ed5157f0ff8c0f2213973f49 *ubuntu-7.04-alternate-i386.iso

[http://nimishbatra.wordpress.com/2007/04/21/downloading-ubuntu-xubuntu-alternate-install-http-and-bittorrent/](http://nimishbatra.wordpress.com/2007/04/21/downloading-ubuntu-xubuntu-alternate-install-http-and-bittorrent/)

actually, i just copy the image from my friend.. and now, i'm still downloading the image.. and 2 more hours to finish it

---

