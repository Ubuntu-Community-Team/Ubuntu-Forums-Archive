---
title: "[SOLVED] boot manager, repeated entry"
date: 2008-06-08
forum: General Help
---

### Post by knull on 2008-06-08
hi, after reinstalling wubi, the kubuntu entry appears twice in my windows boot manager screen, how can i remove the repeated entry? i tried to edit boot.ini but i cant find it, its not on C: (it is not a hidden or system file) also i tried from msconfig but it just shows the windows vista entry

here is my boot manager screen:

windows vista
kubuntu
kubuntu

sorry bad english but its getting better :)

---

### Post by bpl07 on 2008-06-08
It won't show even when you have hidden files shown.  You can open it with the run command.  EasyBCD is another program that is popular for editing the boot file in vista.

Alternatively, you could edit it in ubuntu.  Use Applications > System Tools > NTFS Configuration Tool to mount the XP drive for read/write access (install ntfs-config if you haven't already).  You'll see the boot.ini file.

---

### Post by ago on 2008-06-08
Vista does not use boot.ini. Use EasyBCD.

---

### Post by knull on 2008-06-09
It worked. Thank you both. :)

---

