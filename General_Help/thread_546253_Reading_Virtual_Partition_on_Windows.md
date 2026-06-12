---
title: "Reading Virtual Partition on Windows"
date: 2007-09-08
forum: General Help
---

### Post by runemaste644 on 2007-09-08
I was wondering if i could read my Wubi partition on Windows. Thanks for any help. I think it could be accomplished with a little time in the registry editor.

---

### Post by tuxcantfly on 2007-09-08
explore2fs [http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs)

just tell it to "open disk image" or something like that (it's in the file menu), tell it to open C:\wubi\disks\home.virtual.disk or system.virtual.disk, and you'll be able to access the files

---

### Post by runemaste644 on 2007-09-08
Ok, now i need to know if it is safe and will it corrupt anything

---

### Post by tuxcantfly on 2007-09-08
> Ok, now i need to know if it is safe and will it corrupt anything

Explore2fs is safe and won't corrupt anything; it's read-only though. I'd avoid any of the other Windows-based drivers that have read-write support though, since those could potentially corrupt stuff; instead, should you ever need access to the files in your Wubi loopmounted partitions (if it doesn't boot and you need to repair it), I'd just boot the Ubuntu desktop CD or some other liveCD and follow the instructions here: [https://wiki.ubuntu.com/WubiGuide#head-d08dd29d8d72682732b0bdb835cef9e81cd675b7](https://wiki.ubuntu.com/WubiGuide#head-d08dd29d8d72682732b0bdb835cef9e81cd675b7)

---

### Post by runemaste644 on 2007-09-09
One last question: Does read-only mean i can copy stuff to Windows?

---

### Post by tuxcantfly on 2007-09-09
> **runemaste644 said:**
> One last question: Does read-only mean i can copy stuff to Windows?

yes, but not the other way around (can't write to Ubuntu files from Windows)

---

### Post by runemaste644 on 2007-09-09
Ok thats pretty much all i need to know. Ill try it out soon.

---

