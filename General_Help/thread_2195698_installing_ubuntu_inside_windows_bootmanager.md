---
title: "installing ubuntu inside windows bootmanager"
date: 2013-12-25
forum: General Help
---

### Post by hnf a on 2013-12-25
hi all it's been a while, and i want to install new 13.10 in my laptop, but i want to install it inside windows boot manager i use wubi (is  that good? ) and when boot up the ubuntu jus can't show up the windows boot manager say that the ubuntu can't found in the harddisk? some kind of that. can i install ubuntu from usb inside windows boot manager? and when i go live test the wifi option just don't want to be turned on even my laptop says the wifi has been turned on, i've try using fn button but seem the only fn function that work is just volume,brightness and touchpad, can i turn on my wifi in some way? thank you

---

### Post by oldfred on 2013-12-25
The last supported version of wubi is 12.04. 

Wubi does not work with gpt partitioned drives which all new UEFI systems use.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

[http://askubuntu.com/questions/360616/why-was-wubi-removed-from-13-04](http://askubuntu.com/questions/360616/why-was-wubi-removed-from-13-04)
Wubi does not work on gpt partitioned drives or Window 8 that is pre-installed.
[http://ubuntuforums.org/showpost.php?p=12399988&postcount=2](http://ubuntuforums.org/showpost.php?p=12399988&postcount=2)
Grub4dos (which wubi uses) doesn't work with GPT disks (required by UEFI)
[http://www.omgubuntu.co.uk/2013/04/wubi-advice](http://www.omgubuntu.co.uk/2013/04/wubi-advice)
Wubi not available with 13.04
[https://lists.ubuntu.com/archives/ubuntu-devel/2013-April/036993.html](https://lists.ubuntu.com/archives/ubuntu-devel/2013-April/036993.html)

---

### Post by hnf a on 2013-12-26
first of all thaks for the response, but i think my laptop still using bios ,now just the matter where to install it do you think that using grub is better than using windows boot manager? thaks for reply andhow  about the wifi can you fix it?

---

### Post by oldfred on 2013-12-26
We tend to prefer grub, but then we are a Linux site. 

You cannot just use the Windows boot loader as it does not support multi-booting, but have to install third party boot loaders which usually use grub4dos, an old version of grub that works with Windows formatted drives and forces you to install grub2's boot loader to a PBR - partition boot sector. Forcing grub into a PBR makes it use blocklists as it does not fully fit and it uses hard coded addresses to work. But if any software's address changes then you have to reinstall grub to PBR. Best to have Boot-Repair or know how to manually reinstall grub from live installer. 

Start a new thread on your wifi issues with that in the title and chip model and/or search forum as there are a lot of threads on wifi issues. Often if installed with wired Ethernet it will offer to install correct wireless. See system settings. Depending on version it may be in different places for Software/drivers updates.

---

### Post by hakuna_matata on 2013-12-26
Wubi for 13.10 has no official support. But it is still available: [http://releases.ubuntu.com/saucy/wubi.exe](http://releases.ubuntu.com/saucy/wubi.exe)

IMHO there are not more or less problems than with last supported version including real support.

It is possible to migrate a Wubi install to partition: [https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi) So a Wubi install is not a decision forever.

---

### Post by hnf a on 2013-12-29
ok thanks for the reply all.... now i'll considering using grub as boot loader

---

### Post by Bucky Ball on 2013-12-29
One of the main problems with Wubi (apart from the fact it is no longer supported) is that hardly anyone uses it, so when something goes wrong there is not a lot of help available, even from forum 'gurus'.

Wubi was never intended as a long term solution, more a 'try before you buy' (or install) idea. Never a good one, in my opinion, as you can try the OS from the install media before installing. A relic. ;)

---

