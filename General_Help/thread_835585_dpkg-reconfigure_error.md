---
title: "dpkg-reconfigure error"
date: 2008-06-20
forum: General Help
---

### Post by oguzy on 2008-06-20
Here is what i get at my 8.04 Hardy, Kubuntu. 

$ sudo dpkg-reconfigure -force -phigh xserver-xorg
[sudo] password for oguz:
debconf: unable to initialize frontend: Orce
debconf: (Can't locate Debconf/FrontEnd/Orce.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at (eval 19) line 2.)
debconf: falling back to frontend: Noninteractive
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080620220522

What should i do to get the dpkg-recpnfigure show the dialog box. I tried the dpkg-recpnfigure debconf but it didnt worked.

---

### Post by geirha on 2008-06-20
It doesn't recognize the option "-force", so try with just "sudo dpkg-reconfigure -phigh xserver-xorg".

---

### Post by oguzy on 2008-06-21
It is not working either.

$ sudo dpkg-reconfigure -phigh xserver-xorg
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080621080156
$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04"

---

### Post by Rocket2DMn on 2008-06-21
> **oguzy said:**
> It is not working either.

$ sudo dpkg-reconfigure -phigh xserver-xorg
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080621080156
$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04"

That is normal output there, it is just overwriting the old xorg.conf after making a backup.  You should be good to go.

---

### Post by oguzy on 2008-06-22
But i dont see any dialog screen that asks me questions about keyboard and video.

---

### Post by pietjanjaap on 2008-06-22
8.04 only
sudo dpkg-reconfigure xserver-xorg, works in textmode, but it has change, it does something with the keybord but not videocard/monitor.

Now you have to reboot in safe mode, choose the last option(with the x), now ubuntu wil detect your videocard/monitor.
Then reboot, install your videocard driver(i use envy)

---

