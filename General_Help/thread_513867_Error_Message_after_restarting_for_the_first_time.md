---
title: "Error Message after restarting for the first time"
date: 2007-07-31
forum: General Help
---

### Post by rcronin on 2007-07-31
Hello,
I just restarted the computer to load up ubuntu after the installation. I let it run and get the following message:
Booting 'Ubuntu'

(hd0,0)
Filesystem type is nfts, partition type 0x7
[Linux-bzImage, setup=0x1c00, size=0x1a82cc]
[Linux-initrd @ 0x1f85e000, 0x7918a5 bytes]
Loading, please wait...
[    23.18105] ACPI: count given by _CST is not valid
NO RAID disks
     Check root= bootarg cat /proc/cmdline
     or missing modules, devices: cat /proc/modules ls dev
ALERT! does not exist. Dropping to a shell!


BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs) _

---

### Post by aquavitae on 2007-07-31
> **rcronin said:**
> 
(hd0,0)
Filesystem type is nfts, partition type 0x7

Did you try to install ubuntu on an ntfs partition?  What is you disk setup, i.e. how many hard drives do you have, how are they partitioned and what order are they in (in the bios)

---

### Post by ago on 2007-07-31
try to edit c:\wubi\boot\grub\menu.lst and append "acpi=off" to the line that starts with "kernel"

---

### Post by rcronin on 2007-07-31
Ago,
Editing the menu.lst file worked. It is now installing fine now!
Thank you so much!
-rcronin

---

### Post by ksglp on 2007-08-01
Hi, i'm having similar problems, i'm using a machine where Windows XP was failing to boot, i never did find out why, 

Ubuntu installed ok from a CD, but when i try to boot it up it says;

BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs) _ 

does anyone know how to fix this, or whether it is in fact fixable?

i can't boot into Windows, 

please could you give all advice as though you were speaking to a monkey, because a lot of the time on here i think you think anyone could understand what you were saying, and i normally struggle

cheers,

Jordan

---

### Post by ago on 2007-08-01
Jordan if you cannot boot into windows it might be that you need to run 

chkdsk /f

see for instance [http://support.microsoft.com/kb/315265](http://support.microsoft.com/kb/315265)

PS are you installing using wubi or the Ubuntu CD? The above should not be relevant if you use the standard CD

---

### Post by ksglp on 2007-08-01
I'm using the CD, i can't get into Windows to get onto the internet to download wubi on the computer i'm trying to install it,

so since that's seemingly irrelevant, any other ideas?

thanks for the speedy reply too by the way!

---

### Post by aquavitae on 2007-08-02
>  i can't boot into Windows, 
What exactly happens?  I assume you can select windows xp in the grub boot loader, but does it get as far as the windows logo?
As for ubuntu: I'm sure if fixable, its certainly happened to me lots of times before (usually after I've done something stupid!) and I've managed to get it sorted, just not sure how :) Can you get into a terminal using the second ubuntu boot option... system repair or whatever its called?

---

### Post by ksglp on 2007-08-03
right, what now happens is that i get error 18 when it's booting, i've got past this a couple of times though,

i can access the second option, i tried to repair the grub that way, but that had an error too, the cd check says the cd is fine,

when i do try and load up windows, i actually gets past the xp logo, it loads my desktop background image, but no start bar or icons or anything else, it's effectively just a big expensive photograph

when ubuntu was loading it would get to the ubuntu logo, the loading bar wouldn't progress a millimetre, and after a while the lines i've mentioned appear,

it's getting very annoying, as you can imagine, so if anyone knows a way to get this to work it would be much appreciated, i'd even reformat my hard drive, if you talk me through how to do it right because if i knew how i would have already, there's stuff on there i want, but nothing i need,

please will you also remember to speak to me like the idiot i am, or i will get lost in terminology,

cheers,


Jordan

---

### Post by aquavitae on 2007-08-06
It soulds like the problem with windows is a specific windows proiblem (i.e. nothing to do with linux) and unfortunately I don't know enough about windows to help with that.  Going back to the linux problem, however, that should be solvable.  Reintalling might be the easiest solution, and it would probably be a good idea to back your docs up anyway.  I can give you help with that.  Otherwise we could try to repair the existing installation.  Did you try > try to edit c:\wubi\boot\grub\menu.lst and append "acpi=off" to the line that starts with "kernel"  I don't know if it will help but it might be worth a try.

---

### Post by ago on 2007-08-06
> **ksglp said:**
> Ubuntu installed ok from a CD, but when i try to boot it up it says;

If you installed ubuntu from CD you should use the general forum for support

---

