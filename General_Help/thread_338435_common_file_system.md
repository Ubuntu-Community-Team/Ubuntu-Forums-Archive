---
title: "common file system"
date: 2007-01-14
forum: General Help
---

### Post by phatsteve on 2007-01-14
I dual boot XP and Ubuntu (Edgy) I have a 200gb storage drive (sdb1 in ubuntu, Local Disk (E:) in windows), currently formatted as NTFS. It has all my media files on it. Is there a file system I can convert it to that either OS is happy to read and write to? I don't want to go back to Fat, I've heard a bit about cifs, would that do? Is it easy?

Thanks in advance

---

### Post by taurus on 2007-01-14
To write to ntfs:
[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

To read/write to ext2/ext3:
[http://www.fs-driver.org](http://www.fs-driver.org)

---

### Post by phatsteve on 2007-01-14
Ext2ifs is brilliant! I've just installed it and assigned my ubuntu drive a letter in XP and it shows up straight away in explorer. In view of the warning about ntfs-3g still being in beta and possibly buggy, would it be better to format my storage drive to ext2 for use by both OS's?

---

### Post by taurus on 2007-01-14
You can use ext3 (default filesystem for Ubuntu) with Ext2ifs too.

---

### Post by phatsteve on 2007-01-14
So is ext3 better than ext2? what do you recommend? And thanks for the help so far.

---

### Post by qamelian on 2007-01-14
> **phatsteve said:**
> So is ext3 better than ext2? what do you recommend? And thanks for the help so far.

The ext3 filesystem is essentially ext2 with journaling features to protect the integrity of your data.

---

### Post by taurus on 2007-01-14
> **phatsteve said:**
> So is ext3 better than ext2? what do you recommend? And thanks for the help so far.

Ext3 all the way.

---

### Post by phatsteve on 2007-01-14
Thankyou, ext3 it is. One more question, when I have dumped all my media files on a spare drive (or 2), formatted 200gb drive to etx3 with ubuntu, copied all my files back, will I still be able to share some folders like I do now? so I can access them with my laptop? I realise I will have to install ext2ifs on my laptop.

---

