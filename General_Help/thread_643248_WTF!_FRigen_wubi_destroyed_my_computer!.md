---
title: "WTF! FRigen wubi destroyed my computer!"
date: 2007-12-17
forum: General Help
---

### Post by Bosnian Kralj on 2007-12-17
I tryed installed wubi, and while it was download the .iso part of the installation, i went on youtube, and on aim, and the comptuer froze - so now i restart, but when i restart, it get the error boot up "BOOTMGR is missing..."

So i pop in my windows install disk, and click repair, now comes the part where i have to pick which OS i want to repair...AND THERE'S NO OPERATING OS's ON MY COMPUTER! WTF, Safe mode does nothing, and all i can do is turn on the computer and get that error, now im stuck using this 256mb ram computer!

CAN SOMEONE PLEASE HELP ME!

Contact me via aim, or here please.

---

### Post by ago on 2007-12-17
pop the windows CD, press "r" when you get a the option, you should get a dos prompt
move to the drive where you have wubi/windows (usually c: )
run "chckdsk /r" from the windows CD
type "exit"

---

### Post by Bosnian Kralj on 2007-12-17
To late, I already re-installed vista...These forums are so laggard, you get replies like 8 hours later.

---

### Post by TorontoStorm on 2007-12-18
hey at least you get a good response, don't complain man

---

### Post by GOD-CGS- on 2007-12-22
i have something similar

i was in windows looking on the ubuntu disc before starting install on second drive and accidentally double instead of single clicked wubi-cdboot.exe 

this started an install process in windows that could not be cancelled and then rebooted, i took out the unbuntu disc and all i can get now is 

GRUB loading Stage1.5

GRUB loading, please wait...

ERROR 17.

I cannot even get into windows to fix it

How to I get this back to boot windows 

Things i have tried, booted from ubuntu cd &  
1) putting back boot.ini to normal
2) replacing other 2 boot files for generic
3) deleting all ubuntu files off my hard drive

where is the file that forces my pc to boot grub instead of windows ?

i dont have my windows disc with me to run repair because i am away from home for christmas and my laptop id fu@ked. Yes my lappy has got 2 hard drives its an alienware area 51 m7700 

PLEASE HELP :(

---

### Post by tuxcantfly on 2007-12-23
> **GOD-CGS- said:**
> i have something similar

i was in windows looking on the ubuntu disc before starting install on second drive and accidentally double instead of single clicked wubi-cdboot.exe 

this started an install process in windows that could not be cancelled and then rebooted, i took out the unbuntu disc and all i can get now is 

GRUB loading Stage1.5

GRUB loading, please wait...

ERROR 17.

I cannot even get into windows to fix it

How to I get this back to boot windows 

Things i have tried, booted from ubuntu cd &  
1) putting back boot.ini to normal
2) replacing other 2 boot files for generic
3) deleting all ubuntu files off my hard drive

where is the file that forces my pc to boot grub instead of windows ?

i dont have my windows disc with me to run repair because i am away from home for christmas and my laptop id fu@ked. Yes my lappy has got 2 hard drives its an alienware area 51 m7700 

PLEASE HELP :(

If you happen to have a spare CD or USB flash drive to use, put the super grub disk [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/) on it, and use these instructions to restore the bootloader: [http://supergrub.forjamari.linex.org/?section=documentation#grub_restore](http://supergrub.forjamari.linex.org/?section=documentation#grub_restore)

Or, another way to fix that issue would be to mount your Windows partition and edit the boot.ini, then remove the last line from it (C:\grldr="Ubuntu" or C:\wubildr="Wubi-cdboot" or something along those lines), save, then see if you can boot into Windows

---

