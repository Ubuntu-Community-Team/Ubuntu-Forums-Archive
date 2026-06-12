---
title: "Cannot boot Windows XP"
date: 2007-01-20
forum: General Help
---

### Post by gorannf on 2007-01-20
Hi,

I'm trying to boot Windows XP. So I followed this guide:
[http://ubuntuguide.org/wiki/Ubuntu#How_to_add_Windows_entry_into_GRUB_menu](http://ubuntuguide.org/wiki/Ubuntu#How_to_add_Windows_entry_into_GRUB_menu)
I did all of that and replaced (hd0,0) with (hd0,1) because windows is on hda2, but I still can't boot windows. I get some kind of error when trying to boot it. I'm using ubuntu 5.10. Any suggestions?

Thanx in advance

---

### Post by JamieC on 2007-01-20
If you could quote the error that'd help us a lot more...

---

### Post by gorannf on 2007-01-20
I'm sorry for that. Here it is:

> 
Booting 'Microsoft Windows'
root (hd0,1)
   Filesystem type unknown, partition type 0,7
savedefault
makeactive
chainloader +1

NTLDR is missing
Press ctrl+alt+delete to restart

---

### Post by Error1312 on 2007-01-20
That's not an error from grub, but a windows specific one.

Try this guide to fix it: [http://www.tinyempire.com/shortnotes/files/ntldr_missing.htm](http://www.tinyempire.com/shortnotes/files/ntldr_missing.htm)

---

### Post by JamieC on 2007-01-20
Ignore this post...

---

