---
title: "Uninstalling Ubuntu - GRUB error 12"
date: 2007-06-21
forum: General Help
---

### Post by winterj on 2007-06-21
So i'm switching ubuntu to it's own machine, and now my XP Media center edition won't boot now that i've uninstalled ubuntu.  Here is the screen I have after the BIOS are loaded:

GRUB  Loading stage 1.5

GRUB loading, please wait...
Error 22



Now I've looked up and down through GRUBs documentation on this error but it doesn't seem to go with my problem.  Doing a MBR fix from a windows xp cd isn't possible, as my PC didn't come with one.  So, I suppose my question is how do I get Windows XP Media Center Edition to boot like normal without GRUB or anything, without having a MBR Recovery CD.

Thanks for any information.

---

### Post by LaRoza on 2007-06-21
Good news! Use the Super Grub Disk to restore the Windows mbr, and it will work fine. Check my sig for SGD.

---

### Post by adrian15 on 2007-06-21
> **LaRoza said:**
> Good news! Use the Super Grub Disk to restore the Windows mbr, and it will work fine. Check my sig for SGD.

Change your signature please. The new SGD webpage is: [http://geocities.com/supergrubdisk/]("http://geocities.com/supergrubdisk/").

Thank you.

adrian15

---

### Post by winterj on 2007-06-21
Ok I used that, it seems that i've gotten rid of GRUB and it's mess of problems, but I still can't boot.  Here's the screen I get following initial bios startup:



Windows could not start because of a computer disk hardware configuration problem.

Could not read from the selected boot disk. Check boot path and disk hardware.

Please check the Windows documentation about hardware disk configuration and your hardware reference manuals for additional information.





Here's my boot.ini:


[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect


It looks like the CD corrected my boot.ini to what it should be, so why would windows give me this message at startup?  There's loads of search results on this error but they all tell you to insert your XP cd to fix it, which never came with my computer.

Just one problem after another today!

---

### Post by winterj on 2007-06-21
More Information:

The partition with windows Xp is /dev/sda2 ... Not sure if that means anything I know how XP likes to be the first partition, but as you can see my boot.ini that shouldn't be a problem since it's configured to read off the second.

---

### Post by alienexplorers on 2007-06-22
Put your windows disk in and boot to recovery mode.  Enter fixmbr and exit recovery mode.  Reboot.

---

### Post by Canis familiaris on 2007-06-22
In future if you do not want to use Ubuntu permanently, install it in a Virtual Machine.

---

### Post by Herman on 2007-06-22
Hello winterj,
There are lots of other ways to restore your IPL for Windows in your MBR, I have a web page with a whole collection of different ways, one or two or more of them will solve your problem. Here is the link, [Un-install Page]("http://www.users.bigpond.net.au/hermanzone/p18.htm").

You could try the  [ Windows 98 Floppy Disk Method]("http://www.users.bigpond.net.au/hermanzone/p18.htm#Windows_98_Floppy_Disk_Method"), or use [ MbrFix.exe]("http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe"), or another solution that will work would be to[ use GAG Boot Manager instead.]("http://www.users.bigpond.net.au/hermanzone/p18.htm#GAG_Boot_Manager")

I am sure that at least one of those proposed solutions will solve your problem. Definitely installing GAG Boot Manager will for sure!

Regards, Herman :D

---

