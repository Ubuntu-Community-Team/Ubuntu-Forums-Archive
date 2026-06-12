---
title: "Memory Stick?"
date: 2007-02-11
forum: General Help
---

### Post by kikazaru on 2007-02-11
How do you manually mount a memory stick? 

I have a Shuttle XPC, SN85G4 which has a "6 in 1 Card reader" built in. I guess it's like another USB device. Anyway, when I put my camera's memory stick in it used to automount but for some reason it stopped mounting. Maybe the reader is broken... but I guess its a software problem.

---

### Post by g3k0 on 2007-02-11
Well through a standard USB port you would do this
Create a directory for the purpose (/MyUsb)
 mount /dev/sd1 /MyUsb

then unmount it with 
 umount /MyUsb

Note: it may not be sd1..

---

### Post by kikazaru on 2007-02-12
Thanks for the answer. Maybe it's not a usb device after all... All I have with in /dev/sd* is: 

/dev/sda   /dev/sda2  /dev/sda6  /dev/sda8  /dev/sdb1  /dev/sdb3  /dev/sdd
/dev/sda1  /dev/sda5  /dev/sda7  /dev/sdb   /dev/sdb2  /dev/sdc

I tried mounting them all, and they are all hard drives, or "no medium found". Is there any way I can find out what I should be mounting?

---

