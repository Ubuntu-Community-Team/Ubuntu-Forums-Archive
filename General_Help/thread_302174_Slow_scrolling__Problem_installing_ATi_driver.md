---
title: "Slow scrolling / Problem installing ATi driver"
date: 2006-11-18
forum: General Help
---

### Post by Infil on 2006-11-18
Hi!

I just installed Ubuntu and this is the first time I'm using any Linux distro ever, so please forgive me.

I have the same problem as described in this thread: [http://ubuntuforums.org/showthread.php?p=1720442]("."). I have also installed the latest ATi Drivers for my X1800XT, but there's a problem.

I chose the automatic option and it installed itself. Then I was asked to run (am I using the wrong word?) /usr/bin/aticonfig, and I did. Nothing happened and I soon found out that I should run aticonfig --initial. Then I get this:

osse@osse-desktop:/usr/bin$ aticonfig --initial
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.original-0
aticonfig: Writing to '/etc/X11/xorg.conf' failed. Bad file descriptor.

Since my scrolling problem has not been fixed (contrary to the other guy when he installed the driver) I assume that I have not been able to run aticonfig --initial properly.

Edit: Furthermore, when I click on ATi Control from the Applications menu I get the following error: Failed to execute child process "fireglcontrolpanel" (No such file or directory).

Help?

---

### Post by Infil on 2006-11-19
No one?

---

### Post by nero_86 on 2006-11-19
Try to reinstall driver whit:

./ati-driver-installer-8.31.5.run --buildpkg Ubuntu/edgy (or other release you are using)

make sure you have the linu-restricted-modules installed
then install the package created and:

sudo depmod -a
sudo aticonfig --initial 
sudo aticonfig --overlay-type=Xv

in your /etc/X11/xorg.conf make sure that there are these line

Section "Extensions"
        Option      "Composite" "0"
EndSection

If dont work you can install driver in synaptic. The package are "xorg-driver-fglrx" and if you want but it is not necessary "fglrx-control"

i hope it could be helpfull

---

