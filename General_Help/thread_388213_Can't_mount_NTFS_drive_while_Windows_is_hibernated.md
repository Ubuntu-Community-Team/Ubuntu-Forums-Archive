---
title: "Can't mount NTFS drive while Windows is hibernated"
date: 2007-03-19
forum: General Help
---

### Post by XmaX on 2007-03-19
I am using ntfs-3g for write support on my Windows NTFS harddrive and it works fine. However, when I hibernate Windows, I always get this message while Ubuntu is loading: "Disc was not clearly unmounted", it then checks it, and always fails. Ubuntu boots normally, but I can't acces this drive, even for read-only. Is there any way to mak it work? I don't need write support that much (for the hibernation time at least), but read support would be helpful, as I store most of my stuff there.
 
Also, I use a Windows driver for Ext3 filesystem to be able to use the other partition under Windows. Maybe this has something to do with this?

---

### Post by flip314 on 2007-03-19
Do not mount a drive in one OS, hibernate, then try to mount it in another OS.  This is a great way to corrupt your file system.  I caused a whole lot of trouble on an ext3 partition because I'd mount it in windows, hibernate, then mount it in linux.  You leave all sorts of open handles, possible cached data or file allocation tables that haven't been written back, etc. etc.

Basically, you're lucky that it hasn't succeeded, because what you're attempting has a very high potential of data loss

---

### Post by steve101101 on 2007-03-20
yeah. make sure the computer is on since when it is hibernated the computer is essentially off.

---

