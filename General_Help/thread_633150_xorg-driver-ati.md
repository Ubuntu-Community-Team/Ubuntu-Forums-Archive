---
title: "xorg-driver-ati"
date: 2007-12-06
forum: General Help
---

### Post by KBenk on 2007-12-06
Okay, I've looked for this a lot and I'm sure I'm just missing it, but I'm looking for a howto to install the xorg-driver-ati. Can anyone show me that?

I've got an ATI Radeon mobility 9000 graphics card and I don't think that the fglrx driver is giving me what I need.

Thanks in advance.

~Benk

---

### Post by rbprogrammer on 2007-12-06
i'm no expert on video card, let alone ATI ones..  but have you tried installing the drivers you need with [envy]("http://albertomilone.com/nvidia_scripts1.html")??

i installed my nVidia drivers with easy with that program.  and plus, you will be supporting the guy who made it which i think is a member of the forums..

---

### Post by KBenk on 2007-12-06
I have ENVY installed and when I run it for the ATI Driver I get this:

Envy - Version 0.9.9
Ubuntu Gutsy 32bit
Your graphic card has been detected as a ATI Mobility / Radeon 9000
Your graphic card is supported by the legacy Driver
ENVY ERROR: ATI's legacy driver does not support your operating system

So, I'm guessing ENVY doesn't have the driver I need.

Would it be easier for me to switch operating systems? Would I lose all files and settings that way?

---

### Post by MikeEvans on 2007-12-06
```
sudo dpkg-reconfigure xserver-xorg
```

choose the ATI driver and reboot.

---

### Post by igknighted on 2007-12-06
I would run this command to reinstall it, because the ATI driver likes to overwrite the mesa files that the open-source ati driver needs for 3d acceleration:

```
sudo aptitude purge xorg-driver-ati
sudo aptitude install xorg-driver-ati
```
and then configre as suggested above.

BE AWARE OF WHAT WILL BE REMOVED BY THE FIRST COMMAND!  If it were to try to take all of xorg, you might reconsider this course of action, unless you understand what critical systems are removed and make sure that you get them back.

---

### Post by krazy1912 on 2007-12-06
apt-get install xorg-drivers-fglrx

then go to the restricted drivers manager in your Administration menu and enable the ATI driver.

---

### Post by KBenk on 2007-12-06
Ok. I used ```
sudo dpkg-reconfigure xserver-xorg
``` and it seemed to work. I went through the process and set everything up as well as I could.

Next, You scared me off of trying sudo aptitude purge xorg-drivers-ati but i did run the second command and got this output:

kyle@kyle-laptop:~$ sudo aptitude install xorg-driver-ati
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
Couldn't find any package whose name or description matched "xorg-driver-ati"
The following packages are unused and will be REMOVED:
  liblzo1 
The following packages have been automatically kept back:
  libcompress-zlib-perl 
The following packages have been kept back:
  firefox firefox-gnome-support libmono-cairo1.0-cil libmono-corlib1.0-cil 
  libmono-corlib2.0-cil libmono-data-tds2.0-cil libmono-security2.0-cil 
  libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data2.0-cil 
  libmono-system-web2.0-cil libmono-system1.0-cil libmono-system2.0-cil 
  libmono0 libmono2.0-cil libnm-glib0 libnm-util0 libperl5.8 mono-common 
  mono-gac mono-jit mono-runtime network-manager openoffice.org 
  openoffice.org-base openoffice.org-calc openoffice.org-common 
  openoffice.org-core openoffice.org-draw openoffice.org-evolution 
  openoffice.org-gnome openoffice.org-gtk openoffice.org-impress 
  openoffice.org-java-common openoffice.org-math openoffice.org-style-human 
  openoffice.org-writer perl perl-base perl-modules python-uno 
  ttf-opensymbol tzdata 
0 packages upgraded, 0 newly installed, 1 to remove and 44 not upgraded.
Need to get 0B of archives. After unpacking 201kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 123286 files and directories currently installed.)
Removing liblzo1 ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             


Also, just to see what would happen I used ```
apt-get install xorg-drivers-fglrx
``` and got this output:

kyle@kyle-laptop:~$ sudo apt-get install xorg-drivers-fglrx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xorg-drivers-fglrx


So, do you think I'm set with what I need? How do I make sure?

---

### Post by braacken on 2007-12-07
Another thread on the issue which may assist (specific radeon driver mentioned I think)

[COLOR="Blue"][http://ubuntuforums.org/archive/index.php/t-148531.html[/COLOR]](http://ubuntuforums.org/archive/index.php/t-148531.html[/COLOR])

---

