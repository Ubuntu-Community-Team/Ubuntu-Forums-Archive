---
title: "Wubi"
date: 2017-03-19
forum: General Help
---

### Post by warmango on 2017-03-19
i have an issue with Wubi,
i own a HP Pavilion 533w. i tried to install Wubi without the internet and it failed. when i uninstalled it, i later rebooted i received this error and cant get around it

SYSLINUX 4.04 EDD 2011-04-18 Copyright 1994-2011 H. Peter Anuin et at
No DEFAULT or UI configuration directive can be found!
boot:_



What do i do? i cannot boot back into XP

---

### Post by lisati on 2017-03-19
The bad news is that Wubi is effectively dead, and hasn't been included with Ubuntu for several years.

You might want to consider using a dual-boot instead.

---

### Post by mörgæs on 2017-03-19
> **warmango said:**
> I cannot boot back into XP

Do you want to save XP though it has been out of support for years or do you want to use the space for Buntu?

---

### Post by DuckHook on 2017-03-19
> **mörgæs said:**
> Do you want to save XP though it has been out of support for years or do you want to use the space for Buntu?^^^+1

@OP

It's really not a good idea to be running XP anymore except in a Virtual Machine that is completely isolated from the real world with its virtual NIC disabled.

---

### Post by hakuna_matata on 2017-03-19
> **warmango said:**
> i have an issue with Wubi
IMHO Wubi is not the real reason for that issue.
> **warmango said:**
> 
SYSLINUX 4.04 EDD 2011-04-18 Copyright 1994-2011 H. Peter Anuin et at
No DEFAULT or UI configuration directive can be found!

It is a Syslinux error as described [here]("http://askubuntu.com/questions/30374/boot-failure-no-default-or-ui-configuration-directive-found") but no error caused by Wubi. Maybe, you tried also other methods to install Ubuntu e.g. with a bootable USB drive or you removed manually some files by thinking that they are part of Wubi.

But it is only a guesswork. For a better diagnosis, please run the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") (also available on a Ubuntu [Live_USB]("https://en.wikipedia.org/wiki/Live_USB")/[DVD/CD]("https://en.wikipedia.org/wiki/Live_CD") ). 
> **lisati said:**
> hasn't been included with Ubuntu for several years.
Maybe, it feels like several years ago but it was included with Ubuntu 14.04.5, less than one year ago. see [filelist of ubuntu-14.04.5-desktop-amd64.iso]("http://releases.ubuntu.com/14.04.5/ubuntu-14.04.5-desktop-amd64.list")

---

### Post by lisati on 2017-03-19
> **hakuna_matata said:**
> 
Maybe, it feels like several years ago but it was included with Ubuntu 14.04.5, less than one year ago. see [filelist of ubuntu-14.04.5-desktop-amd64.iso]("http://releases.ubuntu.com/14.04.5/ubuntu-14.04.5-desktop-amd64.list")

Thanks for the update. It has been a lot longer than that since I last used Wubi.

---

### Post by warmango on 2017-03-21
> **hakuna_matata said:**
> 

It is a Syslinux error as described [here]("http://askubuntu.com/questions/30374/boot-failure-no-default-or-ui-configuration-directive-found") but no error caused by Wubi. Maybe, you tried also other methods to install Ubuntu e.g. with a bootable USB drive or you removed manually some files by thinking that they are part of Wubi.

I have been un successful in getting the Tower to boot from any external drive. when I uninstalled Wubi, I used the official Uninstall.exe file

> **mörgæs said:**
> Do you want to save XP though it has been out of support for years or do you want to use the space for Buntu?

I want to Save XP, I am moving files off it to another PC

---

### Post by mörgæs on 2017-03-24
> **warmango said:**
> I have been unsuccessful in getting the Tower to boot from any external drive.

Can't you boot from anything, neither USB nor CD?
What exactly happens when you try?

---

### Post by hakuna_matata on 2017-03-25
> **warmango said:**
> when I uninstalled Wubi, I used the official Uninstall.exe file

The problem of the uninstaller is that it only uninstalls things which Wubi installed before. "[How do I manually uninstall Wubi]("https://wiki.ubuntu.com/WubiGuide#How_do_I_manually_uninstall_Wubi.3F")" contains a list of these things. 

Therefore, it would be possible that... 


[LIST]
[*]You installed Ubuntu with Wubi. 
[*]You installed SYSLINUX. 
[*]SYSLINUX imported existing configuration files into configuration file syslinux.cfg. 
[*]The first menu entry runs the Wubi installed Ubuntu. 
[*]You uninstalled Ubuntu with the Wubi uninstaller. 
[*]The Wubi uninstaller didn't change the SYSLINUX configuration file because Wubi hadn't installed entries to that file. 
[*]Since that SYSLINUX has been failed because of missing the Wubi installed Ubuntu. 
[/LIST]

---

