---
title: "Update and upgrade problem"
date: 2022-08-12
forum: General Help
---

### Post by satimis on 2022-08-12
Hi all,

Ubuntu 20.04 desktop
host of Oracle VirtualBox

On Terminal I just ran;
$ sudo apt update ; sudo apt upgrade

It is very strange to me that it upgrades Ubuntu 20.04 to Ubuntu 22.04

After reboot 

On Terminal
$ sudo apt update```

Hit:1 http://security.ubuntu.com/ubuntu jammy-security InRelease
Hit:2 http://hk.archive.ubuntu.com/ubuntu jammy InRelease
Hit:3 http://hk.archive.ubuntu.com/ubuntu jammy-updates InRelease
Hit:4 http://hk.archive.ubuntu.com/ubuntu jammy-backports InRelease
Reading package lists... Done
Building dependency tree       
Reading state information... Done
560 packages can be upgraded. Run 'apt list --upgradable' to see them.

```

On Terminal again ran;
$ apt list --upgradable > upgradable.txt

I can't attache upgradable.txt file here.  Warning:```

The following errors occurred:

upgradable.txt: Your file of 46.1 KB bytes exceeds the forum's limit of 19.5 KB for this filetype.
```

and
$ sudo apt upgrade```

.....
.....
......
 xdg-desktop-portal xdg-desktop-portal-gtk xserver-xephyr xserver-xorg-core
  xserver-xorg-input-libinput xserver-xorg-input-wacom
  xserver-xorg-video-amdgpu xserver-xorg-video-ati xserver-xorg-video-fbdev
  xserver-xorg-video-intel xserver-xorg-video-nouveau xserver-xorg-video-qxl
  xserver-xorg-video-radeon xserver-xorg-video-vesa xserver-xorg-video-vmware
  yaru-theme-gnome-shell yelp
0 upgraded, 0 newly installed, 0 to remove and 560 not upgraded.

```

$ lsb_release -a```

No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 22.04.1 LTS
Release:        22.04
Codename:       jammy

```

What shall I do with those packages not upgraded ?

Please advise.  Thanks

Regards

---

### Post by oldos2er on 2022-08-12
You can paste large amounts of text to either [https://pastebin.ubuntu.com/](https://pastebin.ubuntu.com/) or [https://pastebin.com/](https://pastebin.com/), then post the link here.

According to your lsb_release results you're running 22.04, not 20.04. The 22.04.1 point release came out recently, which is likely what the large upgrade being offered is.

---

### Post by Impavidus on 2022-08-12
Maybe the upgrade used jammy and jammy-updates, but not jammy-security, or something like that. I found the upgrade from 21.10 to 22.04 the least smooth upgrade in a decade. Anyway, just let apt install the upgrades and hope for the best. Now that you are on 22.04, best to get it proper.

---

### Post by satimis on 2022-08-12
Thanks for your advice.

I have posted the content of upgradable.txt to;
[https://pastebin.ubuntu.com/](https://pastebin.ubuntu.com/) 

The link is here;
[https://pastebin.ubuntu.com/p/K9tvyDd8rb/](https://pastebin.ubuntu.com/p/K9tvyDd8rb/)

Each time running on Terminal;
$ sudo apt update ; sudo apt upgrade ```

.....
.....
vim-common vim-tiny vlc-data vlc-plugin-base vlc-plugin-video-output
  xdg-desktop-portal xdg-desktop-portal-gtk xserver-xephyr xserver-xorg-core
  xserver-xorg-input-libinput xserver-xorg-input-wacom
  xserver-xorg-video-amdgpu xserver-xorg-video-ati xserver-xorg-video-fbdev
  xserver-xorg-video-intel xserver-xorg-video-nouveau xserver-xorg-video-qxl
  xserver-xorg-video-radeon xserver-xorg-video-vesa xserver-xorg-video-vmware
  yaru-theme-gnome-shell yelp
0 upgraded, 0 newly installed, 0 to remove and 560 not upgraded.

```
But I can't upgrade those 560 packages.

How to get rid of it?  Thanks

Besides the most funny thing here is;
There are Ubuntu 20.04 VMs running on this PC.  On their Terminals running;
$ sudo apt update ; sudo apt upgrade

won't upgrade the OS to Ubuntu 22.04.  I don't know WHY?

Please help.  Thanks

Regards

---

### Post by satimis on 2022-08-13
Hi all,

It needs to run "Software Updater" to upgrade to 22.04, not running command on Terminal.

Performed following test on a spare PC
Ubuntu 20.04 desktop
host of Oracle VirtualBox

-> Activities - Software Updater

```

Software Updater
The software on this computer is up to data
However, Ubuntu 22.0.a LTS is now available (you have 20.04)
[Upgrde...] [OK]

```

click [Upgrde...]

-> login as Administrator

```

Release Notes
Welcome to Ubuntu 22.04 'Jammy Jellyfish'
.....
```

click [Upgrade]

Warning```

Third party sources disabled

Some third party entries in your sources.list were disabled. You can re-enable them after the upgrade with the 'software-properties' tool or your package manager.
[closed]

```

-> [Start Upgrade]

Please refer to upload screenshots

After finish -> restarted 

$ lsb_release -a```

No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 22.04.1 LTS
Release:        22.04
Codename:       jammy

```

On Terminal run;
$ sudo apt update```

[sudo] password for satimis: 
Hit:1 [http://hk.archive.ubuntu.com/ubuntu](http://hk.archive.ubuntu.com/ubuntu) jammy InRelease
Hit:2 [http://hk.archive.ubuntu.com/ubuntu](http://hk.archive.ubuntu.com/ubuntu) jammy-updates InRelease
Hit:3 [http://hk.archive.ubuntu.com/ubuntu](http://hk.archive.ubuntu.com/ubuntu) jammy-backports InRelease
Hit:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security InRelease
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
All packages are up to date.

```

No packages held back !!!!!

Also tried on Ubuntu 20.04 VM.  It needs running "Software Updater" to upgrade to 22.04

Regards

---

### Post by kinddolphin8827 on 2022-08-13
You can also grab the  iso image or the thumb drive .img file for the latest release and back up you're important files  and do a fresh installation which inturn would grant you a fresh start and may also clear up some of your issues with certian packages not  upgrading properly. I have had to go the aforementioned route serval time over  in the rwenty0two years I have been using Free and Open source software such as any flavor of Linux or any one of the three BSD distributions.

---

### Post by oldos2er on 2022-08-15
You likely need to run ```
sudo apt full-upgrade
``` to apply all the upgrades.

No, apt upgrade won't upgrade your OS version, it upgrades packages for your current version. It's been like this since day one; it's covered in the man page for apt-get.

---

### Post by satimis on 2022-08-16
Hi all,

Problem solved after runs again "Software Updater"

It asks for "Partially Upgrade"
-> [Yes]

Now the problem mentioned gone.

Thanks

Regards

---

### Post by exelans-41 on 2022-08-16
I had the same problem, I solved it thanks to the comments, thank you[.]("https://weloob.nl/")

---

