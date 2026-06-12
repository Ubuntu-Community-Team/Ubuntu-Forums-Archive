---
title: "dd_rhelp and dd_rescue error:&quot;File too large&quot;"
date: 2008-07-01
forum: General Help
---

### Post by alxbb on 2008-07-01
I have a corrupt filesystem on my Ubuntu partition (it began with error#17) and none of the usual repairs worked. TestDisk failed, giving the error meassage: "filesystem damaged" (I already know that). When trying to rescue the sda1 partition to an external USB hard Drive with dd_rhelp and dd_rescue, I get the error "file too large". Only 4 GB of 40 GB were copied in one particular instance. Does anyone have a solution? Many thanks! Alx

---

### Post by ryanhaigh on 2008-07-01
Sounds like your external drive is formatted as FAT32 which has a 4GB filesize limit. If you want to backup to that drive you will need to format with an alternate filesystem.

---

### Post by alxbb on 2008-07-02
Interesting ... I didn't think about that. The USB drive (WD Passport) is  a blank slate and I can do with it whatever I want. Compatibility with Windows is not an issue. What do you suggest I should do? I am pretty green in that department. Many thanks! Alx

---

### Post by ryanhaigh on 2008-07-02
If your running from the livecd gparted will already be installed (system>admin>partition editor). Just delete any existing partitions on the WD drive and create a new ext3 partition. As always when dealing with partition editing be careful to select the right drives/partitions for deletion.

---

### Post by alxbb on 2008-07-07
Many thanks for your advice! It worked. Created a large ext3 partition on the external usb drive and copied my sda1 with dd_rhelp. Now I have to figure out how to repair the damaged file system (superblocks are bad) but at least all 40GB are backed up now.

---

### Post by zalmoxes on 2008-07-24
i am encountering the same problem. my 1TB external hard disk came formatted as fat32. i didnt know that fat32 has a file size limit of 4gb.


is there a way to convert the existing filesystem to another format without losing the data?


ps: its 60% full. 560gb cant just be put somewhere else and then put back...

---

### Post by ryanhaigh on 2008-07-24
I believe xp has a command line tool that you can use to convert a FAT32 partition into an NTFS partition.

EDIT: [http://technet.microsoft.com/en-us/library/bb456984(TechNet.10).aspx]("http://technet.microsoft.com/en-us/library/bb456984(TechNet.10).aspx")

The other option is to resize the fat partition and make a second partition on the drive using whatever filesystem you like.

Any time you are messing with partitions and filesystems you are risking your data and you really should create a backup of anything you can't afford to lose.

---

