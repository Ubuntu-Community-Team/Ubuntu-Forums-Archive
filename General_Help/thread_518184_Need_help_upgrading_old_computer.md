---
title: "Need help upgrading old computer"
date: 2007-08-05
forum: General Help
---

### Post by cmp1988 on 2007-08-05
Hello, I've got some questions I'd like answered about upgrading the recent install of Dapper on my mom's computer to Edgy or Feisty (Xubuntu). 

Computer: 

IBM Aptiva
P2 450 MHz
256 MB RAM
Nvidia Riva 128ZX Graphic Card with 8 MB Video Memory
20 GB Hard Drive
Xubuntu Dapper (Lone OS)
~900 MB Swap, rest to "/"


1. Wireless Card.  It's a Netgear WG111 v2 that needs the Ndiswrapper install to run.  How will an OS upgrade affect that?
2. I tried Feisty install the first time around, and it fought me every step of the way.  I had to restart X several times to get the LiveCD environment to work properly, then I had snags at the install.  The snags were basically not wanting to wipe the CD through the install, so I had to do it separately with Gparted.  The install did manage to complete.  However, the computer still ran slower than a Windows that has a few months under its belt, and wouldn't recognize things.  It did say that the BIOS was past the "Cutoff" date (BIOS is 1999, cutoff is 2000) for something.  Anyway, it was a very tough experience to have Feisty, so I downgraded it to Dapper, and that worked without a hitch.  Anyway, I'm wondering if anyone has Feisty on a computer 1999 or older, by LiveCD or Upgrade.

3. Will an upgrade break the current install on such an old computer?

The reason I want to upgrade is the updated repos.  If I can get up-to-date repos for Dapper, doesn't matter if they're Debian repos or whatever, then I wouldn't have as much incentive for Upgrading.  If I could get updated repos, that'd be great, because I wouldn't have to mess around with the OS and break anything.

---

### Post by kerry_s on 2007-08-05
you should do a custom debian install. since you got almost the same specs as mine, i recommend debian custom(base)+icewm+rox it is fast. every now and then i just do apt-get update and apt-get dist-upgrade and i'm fully up to date. no more installing again and again just to keep up with the latest. a little advice, stick with the 2.6.18 kernel it runs the best on old rigs, another plus, debian does not drop support for are old gear like ubuntu does, another thing is debian still uses separate kernels so you can pick the 1 for your processor.
 
the pretty installer, type> installgui 
(i use> install vga=791 <which sets the screen to 1024x768 text install, just what i prefer)

just in case you don't want to try custom, here's the debian xfce4 version->
[http://mirrors.kernel.org/debian-cd/4.0_r0/i386/iso-cd/debian-40r0-i386-xfce-CD-1.iso](http://mirrors.kernel.org/debian-cd/4.0_r0/i386/iso-cd/debian-40r0-i386-xfce-CD-1.iso)

if you want to try a custom->
[http://mirrors.kernel.org/debian-cd/4.0_r0/i386/iso-cd/debian-40r0-i386-businesscard.iso](http://mirrors.kernel.org/debian-cd/4.0_r0/i386/iso-cd/debian-40r0-i386-businesscard.iso)

start the install, when it comes to package selection, uncheck them all.
after reboot
log in as root
apt-get install xorg gdm synaptic icewm rox-filer leafpad iceweasel
reboot(ctrl+alt+delete)
select icewm in the session menu and login
open synaptic and continue building to your mom's needs

(i'll put a pic in a sec, i'm messing with jwm right now)
1 is icewm, 2 is jwm

---

### Post by cmp1988 on 2007-08-05
That's interesting, but how bouts the Ndiswrapper thingy for the internet?  Can't apt-get anything without internet.  Is there Ndiswrapper Package in there somewhere?

---

### Post by kerry_s on 2007-08-05
ubuntu doesn't come with ndiswrapper either, i assumed(the mother of all screw ups :) ) you was going to plug it in to install since wireless is not the best for installing, you get dropped and unexpected things can happen. in debian you can install ndisgtk, it's the graphical ndiswrapper, then just point and click to install your driver, after you install first of course.

---

