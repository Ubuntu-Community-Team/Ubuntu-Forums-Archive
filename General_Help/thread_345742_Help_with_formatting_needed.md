---
title: "Help with formatting needed"
date: 2007-01-24
forum: General Help
---

### Post by Hickeydog on 2007-01-24
Okkk.  I wanted to be able to see the ubuntu partion under windows XP on my computer.  Sooo, I came up with the brilliant plan: Reinstall Ubuntu and use NTFS as the format for "/'  so I pop in the Live CD and go to install it only to find out that "/" cannot be in the NTFS format.  I thought "ok no biggie.  I just wanted to try it." so I go back and tell the installer to format it using the ext3 format.  I get that done and try to install Ubuntu only to find out that my "/" partition IS STILL NTFS!!!!!!! :mad: :mad: I have tried deleting that partition and reformatting it, but is alway comes up as NTFS.  I need to get rid of it so I can format it as the ext3 so I can install Ubuntu

---

### Post by Hickeydog on 2007-01-24
I ddin't mean to put it here.  I thought I was in General Help.  SORRY!!!!!!. 
If one of the admins could move this to General Help, that would be greatly appreciated. 
I am such a noob

---

### Post by Hickeydog on 2007-01-24
Never Mind!!! I Got It Too Work!!!!!!!!!

---

### Post by taurus on 2007-01-24
Use gparted from the LiveCD to reformat it to ext3 first.  Then, click the Install icon to install it.  And if you want to read and write to Ubuntu (ext2/ext3) from Windows, just install fs-driver in Windows and everything is peachy...

[http://www.fs-driver.org](http://www.fs-driver.org)

---

