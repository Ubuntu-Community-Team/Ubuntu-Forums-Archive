---
title: "Can't Boot after 14.04.1 LTS Update"
date: 2014-08-27
forum: General Help
---

### Post by rossjam78 on 2014-08-27
I recently tried to upgrade from Ubuntu 12 to 14 LTS, but after my laptop rebooted, it was unable to boot ubuntu.  I can however boot Windows 7, whcih was the first operating system on the laptop.  I have read several of the threads in this forum and tried a couple of the suggestions, but from what I can tell my problem is different.  I created a live USB to poke around and see if I could diagnose anything, but I think I'm in over my head.  I ran the boot info script from source forge, and I didn't see any red flags in it, but I am attaching the results file in case I am wrong (and it is compressed because it was just too big otherwise).  After that I took a closer look at the error message that is displaying when booting fails:  "Gave up waiting for root . . . Alert!  /dev/disk/by-uuid/b4c0ca32-c142-46bc-b77e-22a06d884b9a does not exist."  Well, the uuid it is showing there is right for the partition that Ubuntu is installed in, but as it turns out, there is no /dev/disk directory in that install.  How that happened, I don't know.  There were no errors or warnings during the install.  I also looked into what was in that directory on my live USB and it is a link to the file /dev/sda5 (again the correct partition) and this file is also missing on the broken install of Ubuntu.  I have no idea how to replace the missing files and I don't even know if that is the full extent of the problem.  I am also attaching a file called sda5dev that is a capture of ls for /dev on the hard drive and a file called sdbdev that is an identical capture for the live USB.  I have been trying to compare and contrast them to see if anything else is missing, but I don't know if that is important.  Any advice or help that can keep me from having to wipe out everything I had and start from scratch would be very much appreciated. 
 [ATTACH]255867[/ATTACH]
[ATTACH]255868[/ATTACH]
[ATTACH]255869[/ATTACH]

---

### Post by fantab on 2014-08-27
Assuming that you have not poked into any other issues, reinstalling Grub with Ubuntu Live DVD/USB should make the system boot again.
You can do this quite easily with [boot-repair tool]("https://help.ubuntu.com/community/Boot-Repair").

---

### Post by rossjam78 on 2014-08-27
Unfortunately, the boot repair tool didn't solve the problem.  I'm still getting the same error message and still can't boot anything but windows.  I guess this means the grub wasn't the problem, which is good to know.  Also, the url the boot repair tool gave me is [http://paste.ubuntu.com/8164771/](http://paste.ubuntu.com/8164771/)

Thanks for the suggestion too

---

### Post by fantab on 2014-08-28
Are you booting with USB plugged in? Sometimes this can cause problems if USB boot is enabled and prioritized in BIOS.
The boot-info seems alright... 

What machine are you on...? on some laptops the 'brightness' setting need to be changed.
What kind of Graphics?

---

### Post by diyhouse on 2014-08-28
I too had grub problems,.. I did a clean install of mythbuntu 14.04,..  once I got a stable system I created a backup using the following...
---
dd if=/dev/sda1 conv=sync,noerror bs=64K | gzip -c  > /mnt/disky/OS-disk/sysimage-sda1-23May14.img.gz
---
Thus creating a snap-shot of my system

After some further playing with myth,.. (loaded some big tools via apt-get) decided to go back to prvious snap-shot. using 
---
gunzip -c /mnt/disky/OS-disk/sysimage-sda1-XXyyy14.img.gz | dd of=/dev/sda1 conv=sync bs=64K
---
When I tried to reboot back into myth,.. GRUB failure!!! "error: file /boot/grub/i386-pc/normal.mod not found",

A quick search pointed me to some fixes about boot from DVD, mounting file system and reloading GRUB, This I tried but could not mount file system as it was corrupt, even tried a fsck,.. and just got too many errors,..(ouch!), So forced to reload and rebuild.

([http://askubuntu.com/questions/266429/error-file-grub-i386-pc-normal-mod-not-found](http://askubuntu.com/questions/266429/error-file-grub-i386-pc-normal-mod-not-found))

OK so I have a working system again,.. but unable to restore snap-shots,.. can anyone help as to how I can fix this little quirk, as I would regularly restore snap-shots when configuring system and I made a mistake or I did not like something.

---

### Post by rossjam78 on 2014-08-28
I ran the boot info script from a live USB but the install of ubuntu that is not working is on my hard drvie.  So far, I have not tried booting to the hard drive while my live USB is plugged in.  My laptop is a Dell Inspiron N7010 (about 4 years old) and the only driver problem I have had so far was with my wireless radio/network card working with Ubuntu 12.  I am using the live USB right now and the system settings calls my graphics card an Intel Ironlake Mobile.

---

### Post by claracc on 2014-08-29
> **diyhouse said:**
> I too had grub problems,.. I did a clean install of mythbuntu 14.04,..  once I got a stable system I created a backup using the following...
---
dd if=/dev/sda1 conv=sync,noerror bs=64K | gzip -c  > /mnt/disky/OS-disk/sysimage-sda1-23May14.img.gz
---
Thus creating a snap-shot of my system

After some further playing with myth,.. (loaded some big tools via apt-get) decided to go back to prvious snap-shot. using 
---
gunzip -c /mnt/disky/OS-disk/sysimage-sda1-XXyyy14.img.gz | dd of=/dev/sda1 conv=sync bs=64K
---
When I tried to reboot back into myth,.. GRUB failure!!! "error: file /boot/grub/i386-pc/normal.mod not found",

A quick search pointed me to some fixes about boot from DVD, mounting file system and reloading GRUB, This I tried but could not mount file system as it was corrupt, even tried a fsck,.. and just got too many errors,..(ouch!), So forced to reload and rebuild.

([http://askubuntu.com/questions/266429/error-file-grub-i386-pc-normal-mod-not-found](http://askubuntu.com/questions/266429/error-file-grub-i386-pc-normal-mod-not-found))

OK so I have a working system again,.. but unable to restore snap-shots,.. can anyone help as to how I can fix this little quirk, as I would regularly restore snap-shots when configuring system and I made a mistake or I did not like something.

I suggest you open your own thread for your problem with a descriptive title.

---

### Post by diyhouse on 2014-08-29
Duly done,.. I assumed they were related issues,. sorry for confusing things.

---

### Post by rossjam78 on 2014-09-08
Well, since I still have not found a workable solution, I am just going to install a fresh copy of Ubuntu 14.04.1 LTS.  Since this "solves" my problem, I am marking this thread as solved.  Thanks again to everyone that helped me look for a solution.

---

