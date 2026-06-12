---
title: "Error 14: Invalid or unsupported executable format"
date: 2007-05-14
forum: General Help
---

### Post by blackjackel on 2007-05-14
Alright, this is what happned:

I installed wubi, restarted, and got error 17.... So I uninstall wubi, reinstall, and now I get error 14.

Another problem I have is that I can not change any of the wubi settings when I click on advanced settings, so I can't try and run it from the first partition on my 2nd drive instead of the 2nd partition.

Any help appreciated.

Here is what I see on the screen:

Booting 'Ubuntu'

find --set-root --ignore-floppies /wubi/boot/linux

Warning: MBR cyinders(19930) is not equal to the BIOS one(16383).

Warning: MBR total sectors(320175450) is greater than the BIOS one(320173056).
Some buggy BIOSes could hang when you access sectors exceeding the BIOS limit.
(hd1,4)
Filesystem type is ntfs, partition type 0x7
kernel /wubi/boot/linux find=/wubi/boot/linux/ quiet ro


Warning: MBR cyinders(19930) is not equal to the BIOS one(16383).


Warning: MBR total sectors(320175450) is greater than the BIOS one(320173056).
Some buggy BIOSes could hang when you access sectors exceeding the BIOS limit.

Error 14: Invalid or unsupported executable format

Press any key to continue...

---

### Post by ago on 2007-05-14
> **blackjackel said:**
> Alright, this is what happned:

I installed wubi, restarted, and got error 17.... So I uninstall wubi, reinstall, and now I get error 14.
That's a first, is that wubi test2? Bean123 is working on a patch for grub. Be patient there.

> Another problem I have is that I can not change any of the wubi settings when I click on advanced settings, so I can't try and run it from the first partition on my 2nd drive instead of the 2nd partition.
That's because you are in reinstall mode. Choose uninstall and then Install again. Also make sure that your partition is defragemented and uncompressed and that all your virtual drives are <= 4GB. 

You can also try to use a different program to generate the virtual disks, like qemu-img (just replace them before rebooting).

---

### Post by blackjackel on 2007-05-14
I just wanted to clarify about the settings in the wubi installation. None of the scroll down menus work... I can't change language on the first screen, and when I click settings, I can't change any of the options there either.

When I click an arrow (that should give me a scroll down menu) I get what looks like an empty menu.... I see two pixels below the default (i assume this is the empty menu). This is very odd.

---

### Post by ago on 2007-05-14
> **blackjackel said:**
> When I click an arrow (that should give me a scroll down menu) I get what looks like an empty menu.... I see two pixels below the default (i assume this is the empty menu). This is very odd.

Yes indeed. Is this for all the dropdowns or only for the disk size ones? The distro dropdown for instance is it ok?

---

### Post by blackjackel on 2007-05-14
> **ago said:**
> That's a first, is that wubi test2? Bean123 is working on a patch for grub. Be patient there.


That's because you are in reinstall mode. Choose uninstall and then Install again. Also make sure that your partition is defragemented and uncompressed and that all your virtual drives are <= 4GB. 

You can also try to use a different program to generate the virtual disks, like qemu-img (just replace them before rebooting).

Yep, thats wubi test2

I followed your advice, I uninstalled wubi using the uninstall.exe, it removed all files and folders except for the install folder and the .iso file inside it. When I click on the wubi test2 it still does not allow me to change any of the menus, I get what I described above.

---

### Post by blackjackel on 2007-05-14
> **ago said:**
> Yes indeed. Is this for all the dropdowns or only for the disk size ones? The distro dropdown for instance is it ok?

ANY and ALL drop downs, including the language dropdown on the very first sceen I see when running the installer.

---

### Post by ago on 2007-05-14
Hmm never seen that before. 

Anything peculiar about your windows installation you can think of? Any error message when you run wubi (before rebooting)? Do you see virtual disks of appropriate size in C:\wubi\disks?

---

### Post by ago on 2007-05-14
What is your default locale/language in windows?

---

### Post by blackjackel on 2007-05-14
default language/locale is English (United States)

My windows installation is very peculiar, it's installed on the 5th partition on a harddrive with 6 partitions. Though I get no errors when running wubi. The virtual disk is of an appropriate size considering that the default option in settings is 3gb and the disks folder is 3.41GB

Oh, and i'm installing on J: (2nd partition on 2nd hard drive) only because I can't change the drive in the default settings..... Are there registry entries or maybe config files I can edit to change the defaults? 


Lastly, and this has nothing to do with the above, but good job with your lupin the 3rd avatar... I get it, loopin loop installer, lupin the 3rd... :P

---

### Post by ago on 2007-05-14
> **blackjackel said:**
> Oh, and i'm installing on J: (2nd partition on 2nd hard drive) only because I can't change the drive in the default settings..... Are there registry entries or maybe config files I can edit to change the defaults?
If you are in reinstall mode you cannot choose that, otherwise if you uninstall and install you "normally" can. The trick is to install normally, then edit HKLM\software\ms\windows\uninstall\wubi\ and set all the keys there to point to wherevere you want. Then move the wubi folder and run wubi again. This time chooce reinstall mode. It should get the right drive. But you can also simply move the folder to a different partition (note: that may crash wubi installer in subsequent goes). Make sure your boot.ini has a line like "C:\grldr=Ubuntu". The letter there has to be always C: whatever is the drive you are installing to.

---

### Post by blackjackel on 2007-05-14
I followed your advice, installed, edited the registry settings, reinstalled, and now I'm happy to report that I'm witnessing the Ubuntu install process "Select and install software" currently at 54%. Thanks for your help.

---

### Post by blackjackel on 2007-05-23
> **blackjackel said:**
> ANY and ALL drop downs, including the language dropdown on the very first sceen I see when running the installer.

I have FIGURED OUT the problem for this inability to change wubi settings.

It is windows 2000 specific.

I have ran WUBI on 3 computers with windows 2000 and 2 computers with windows XP. All windows XP computers are able to select the dropdowns while the three windows 2000 computers were not able to select the dropdown menus.

it is DEFINATELY a windows 2000 bug.


:D

---

