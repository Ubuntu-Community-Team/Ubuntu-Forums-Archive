---
title: "Changing READ ONLY to WRITE"
date: 2007-04-22
forum: General Help
---

### Post by Mrlush123 on 2007-04-22
I have a seperate HD that I had saved many files when I had windows installed. I am able to read files but all the files there are READ ONLY. 

If I try to edit anything I am not able to write. I go into permission and it says I am not the owner and cannot change permission. What can I do to make the entire harddrive work like a regular drive that I can also save and edit my files. I am new to this as you can see.

:confused:

---

### Post by taurus on 2007-04-22
Is that harddrive a ntfs, a vfat/fat32, or an ext3 filesystem?

---

### Post by bananabob on 2007-04-22
You should check that the device is mounted RW. You can look in /etc/fstab for that.

---

### Post by Mrlush123 on 2007-04-26
It is NTFS...

---

### Post by taurus on 2007-04-26
Then you need to install ntfs-3g driver.

[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

---

