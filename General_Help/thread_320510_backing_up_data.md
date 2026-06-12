---
title: "backing up data"
date: 2006-12-17
forum: General Help
---

### Post by Patrick-Ruff on 2006-12-17
Hey all. I recently found out that my ATI card (a Mobility Radeon X300 PCIe 64MB) will run aiglx. but I have already installed Xgl and fglrx.  I'm running ubuntu edgy, and I have already installed a LOT of packages.

and changes a lot about the system.  I am on dial-up and I don't want to have to reinstall all this stuff again, really. so, I was wondering if there is a way to uninstall xgl packages, fglrx, and still run aiglx perfectly . . . but I don't think it'll work well so heres what I would like to do . . .

I want to backup all the programs and most of the settings so I can apply them to a fresh install and hopefully get back to everything without spending 8 hours fixing everything up.

is it possible to do this?

---

### Post by aysiu on 2006-12-17
Try this:
[Howto: Backup and restore your system!](http://ubuntuforums.org/showthread.php?t=35087)

---

### Post by Patrick-Ruff on 2006-12-17
eh, I don't think I want to try that . . . really. I need to know though, what directories do I have to back up if I want to keep all the programs and updates I have installed, as well as my settings (except video related stuff)

---

### Post by Patrick-Ruff on 2006-12-17
because if I straightup back up everything and redo it it will be killing the purpose of a clean install . . . I only want some things, like the latest updates and my gnome settings and all the programs I have installed. the only reason I'm doing this is because I installed xgl and fglrx, and those are known to conflict with many things when trying to get aiglx working with the normal radeon driver.   and it doesn't seem like I'll be able to uninstall them perfectly . . .

---

### Post by aysiu on 2006-12-17
Well, the problem is really that things kind of live everywhere... programs will install some files to /usr, some to /lib, some to /etc. All your personal settings, however, install to your /home directory.

You haven't cleaned out your /var/cache/apt/archives directory, have you?

If not, I would suggest backing up all those .deb files and creating a separate /home partition:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Once you've done that, you can reinstall and mount your /home partition without reformatting it. Then copy all the .deb files to your desktop and do this: ```
cd ~/Desktop
sudo dpkg -i *.deb
``` That should install all the programs you had in before.

---

### Post by Azakus on 2006-12-17
There is a program in the Ubuntu Repos for a graphical client called Bacula. Haven't tried it myself, but give it a shot if you like.

---

### Post by chalex on 2006-12-17
summary: you want the debs from /var/apt/archive, and you want to back up your /home.

You probably also want a copy of /etc/X11/xorg.conf

---

### Post by Patrick-Ruff on 2006-12-17
the xorg conf, no. the basis of my backing up is my installation of fglrx and xgl. I like asyiu's suggestion best. I'll check it out and clear out the packages I don't want. thanks a bunch I'll let you guys know if it all works out.

---

