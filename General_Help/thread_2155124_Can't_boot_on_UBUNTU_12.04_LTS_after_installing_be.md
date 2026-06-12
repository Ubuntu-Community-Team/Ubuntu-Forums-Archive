---
title: "Can't boot on UBUNTU 12.04 LTS after installing beside Windows 7"
date: 2013-06-17
forum: General Help
---

### Post by faissalman on 2013-06-17
Hello all ubuntu forum members;
After working with the ubuntu liveCD for couple days i decided to install it beside windows 7, so i resize my HDD to 3 partitions, the third one ~40Gio is where i wanted to install ubuntu, i runed with the LiveCD again and choose "install ubuntu", then they ask me to choose between replacing windows 7 or other options, i choose other options of corse. then they showed me all the disks and partitions i have, i select the third partition and delete and creat 3 new partiotions from it, one with 1Gio for booting options i think (sda5) and i selected it in the last field when they ask about the boot option partition, the second one with 2Gio as a swap partiotion, and the third one with 37Gio as ext4 and "/" for the mounting option.

after completing the installation i rebooted my laptop, but it booted on the Windows 7 directly without giving me to choose!!!

Any idea??!!

---

### Post by eduseeker on 2013-06-17
I, too, am an absolute beginner with Linux and myself had experienced the same (with Ubuntu 11.04 and win 8). I don't have solution for your problem but you may try, as an alternative, version 12.10 (or above).

---

### Post by Impavidus on 2013-06-17
There is a problem with Ubuntu 11.04 and secure boot, and therefore it doesn't work well on machines with preinstalled win8. Ubuntu 12.04.2 and up should work. As all versions before 12.04 are end of live you shouldn't install them anyway.

But the OP is dual booting with win7, so that's something different. It seems grub didn't install correctly. Can you boot from the live disk and run [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")? It may fix your problem at once, or it can provide us with a BootInfo summary with more details to help you. Also, which Ubuntu version did you install?

---

### Post by 3rdalbum on 2013-06-17
> **faissalman said:**
> Hello all ubuntu forum members;
After working with the ubuntu liveCD for couple days i decided to install it beside windows 7, so i resize my HDD to 3 partitions, the third one ~40Gio is where i wanted to install ubuntu, i runed with the LiveCD again and choose "install ubuntu", then they ask me to choose between replacing windows 7 or other options, i choose other options of corse. then they showed me all the disks and partitions i have, i select the third partition and delete and creat 3 new partiotions from it, one with 1Gio for booting options i think (sda5) and i selected it in the last field when they ask about the boot option partition, the second one with 2Gio as a swap partiotion, and the third one with 37Gio as ext4 and "/" for the mounting option.

after completing the installation i rebooted my laptop, but it booted on the Windows 7 directly without giving me to choose!!!

Any idea??!!

Boot Repair may sort things out - Impavidus posted a link to it. I would try that first.

Another possibility is that your BIOS is set to boot from the Windows partition, which doesn't contain Ubuntu's GRUB bootloader.

If you can go into your BIOS and see what options you have there to boot from a different disk or partition. If the BIOS can be set to boot from a particular partition, then try changing it to one of the other partitions. The GRUB bootloader might be there, and it will display a menu that allows you to boot Windows or Ubuntu.

---

### Post by faissalman on 2013-06-17
i said i'm using UBUNTU 12.04 LTS
i installed boot-repair and i'm gonna restart now to see if it is solved
here is the BootInfo they give me: [http://paste.ubuntu.com/5773658/](http://paste.ubuntu.com/5773658/)

---

### Post by faissalman on 2013-06-17
Hi guys, boot-repair has succefully fixed my problem, grub works fine now, but about the 1Gio partition i created "/dos" ( for mounting or booting option ) , when i was waiting for your help i formated it from fat32 to ext4.. so when i run ubuntu, a message said "the disk /dos isn't mounted or... press S to ignore mounting or M to manually recover"...
did someone know what to do?!

---

### Post by faissalman on 2013-06-18
Thanks for everyone here.. i just reinstall ubuntu again, all is fine now, just un the boot it wait for me to mount the /tmp, after a while it complete starting, that's all and thank you again ;)

---

