---
title: "Error booting into win8 GRUB2.0 installation, have to go boot through recovery mode"
date: 2012-12-13
forum: General Help
---

### Post by jh0720 on 2012-12-13
Hi, I have a lenovo windows 8 laptop I just purchased (UEFI). I ran boot-repair to give me grub on my system and it runs on bootup. However, ...

On bootup, it shows this image for grub (i'm assuming normal):
[IMG]http://imageshack.us/a/img803/5074/20121213032328.jpg[/IMG]

But when I try to click on "Windows 8 (loader)", I get this error (click windows recovery enironment (loader) gives the same error...only Windows UEFI recovery lets my into win8):
[IMG]http://img805.imageshack.us/img805/9232/20121213032540.jpg[/IMG]

The only way I can get into win8 is by going through recovery mode.

Also, I get this glitchy graphics screen (and constantly "the application Compiz has closed unexpectedly), so I'm guessing there's something wrong with my graphics card? I'm not sure how to fix this:
[IMG]http://imageshack.us/a/img826/3822/20121213032353.jpg[/IMG]

here is my pastebin after I ran boot-repair:
[http://paste.ubuntu.com/1429465/](http://paste.ubuntu.com/1429465/)

thanks!

ps: i found this that's probably related to my question: [http://ubuntuforums.org/showthread.php?t=1904422](http://ubuntuforums.org/showthread.php?t=1904422)

it mentions something about MBR and i'm pretty sure I didn't install it that way. What should I have done?

---

### Post by oldfred on 2012-12-13
Grub creates wrong style chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
These entries by grub will never work.
'Windows ...) (on /dev/sdXY)'


The entries by Boot-Repair should work. Not sure why he now has recovery in the description. But does the first entry (Windows UEFI Recovery)  correctly boot into Windows?


What system and what video card?

---

### Post by jh0720 on 2012-12-14
Yeah, the first entry (windows UEFI recovery) is the only one that works. What should I do about this? I completely uninstalled ubuntu. Is there a different way I should go about installing it for UEFI systems?

The way I installed it was just with "another way" instead of "install ubuntu along with windows 8" and created a /swap logical and a primary in "/" and that's it. GRUB wasn't installed, so I went through "try ubuntu" from my bootable USB and ran boot-repair which installed GRUB

I have a lenovo Y500 laptop (similar to Y580) with a nVidia GT 650m 2GB

---

### Post by oldfred on 2012-12-14
If you have Windows 8 pre-installed you have gpt partitioning not MBR. Then all partitions are the same or in effect primary. 

       Systems need quick boot or fast boot turned off in UEFI settings. Some systems install with secure boot on, some need it off to install. A few do not install at all, but those seem to be bugs in UEFI not Ubuntu.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)

    
You need to use 64 bit version of 12.10 and from UEFI menu boot in UEFI mode. Both Windows & Ubuntu have to be in UEFI mode and how you boot installer is how it installs. Do not boot in BIOS/legacy/AHCI or whatever else option is shown.

older UEFI with Windows 7 so no secure boot issues.
       How to install Ubuntu 11.10 on a Lenovo (U)EFI system (tested on S205, B570)
[http://ubuntuforums.org/showthread.php?t=1867367](http://ubuntuforums.org/showthread.php?t=1867367)

---

