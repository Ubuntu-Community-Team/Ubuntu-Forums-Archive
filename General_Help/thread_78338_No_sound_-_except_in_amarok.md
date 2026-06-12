---
title: "No sound - except in amarok"
date: 2005-10-18
forum: General Help
---

### Post by dcer on 2005-10-18
Hi.

I'm rather new to linux and recently installed breezy, but now I'm left with no sound in any applications, games I tried - except amarok. I understand amarok uses a different sound system than the rest, because it's for kde - maybe that's why it's messed up. I'd really like to keep amarok, but also have the other sounds working too. The sounds worked on a fresh install and I also checked the alsamixer settings... And I checked the multimedia systems selecter which is set to esd and produces sound if I test it. I tried running games also from the terminal to no avail, vlc won't produce any sound either. Please help.

---

### Post by tmadsen on 2005-10-18
Don't know if this is what you're talking about, but there's a guide to installing codecs and stuff on ubuntu wiki: 

[https://wiki.ubuntu.com/RestrictedFormats?action=show]("https://wiki.ubuntu.com/RestrictedFormats?action=show")

---

### Post by dcer on 2005-10-18
Thanks for the reply. I followed the instructions, but it says there's no candidate for w32codecs to install after I added deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) etch main to sources and typed apt-get install w32codecs

I get this from synaptic:

W: GPG error: [http://si.archive.ubuntu.com](http://si.archive.ubuntu.com) breezy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

[ftp://ftp.nerim.net/debian-marillat/dists/etch/Release.gpg:](ftp://ftp.nerim.net/debian-marillat/dists/etch/Release.gpg:) Ni mogo&#269;e za&#269;eti povezave z ftp.nerim.net:21 (2001:7a8:1:5::14). - connect (101 Network is unreachable) [IP: 2001:7a8:1:5::14 21]

[ftp://ftp.nerim.net/debian-marillat/dists/etch/main/binary-i386/Packages.gz:](ftp://ftp.nerim.net/debian-marillat/dists/etch/main/binary-i386/Packages.gz:) Ni mogo&#269;e za&#269;eti povezave z ftp.nerim.net:21 (2001:7a8:1:5::14). - connect (101 Network is unreachable) [IP: 2001:7a8:1:5::14 21]

---

### Post by tmadsen on 2005-10-18
Hm, weird ... I'm getting the same error with the public key now when trying to sudo apt-get update ... when I did it first time around it worked beautifully

---

### Post by dcer on 2005-10-18
The problem can't be only that anyway, cause I don't get any system sounds either. I'll try dumping amarok, but it probably won't make a difference :(

---

### Post by dcer on 2005-10-18
Yay, after removing amarok and rebooting I got system sounds back and vlc works also. But no sounds in games.

Is there a way I could keep amarok without moving to kde and having sounds work, cause I preffer gnome as the desktop?

Maybe I just messed up somewhere and it works otherwise :(

---

