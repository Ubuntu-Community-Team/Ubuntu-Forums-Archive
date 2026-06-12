---
title: "[SOLVED] Mounting ext3 partition in home directory"
date: 2008-06-09
forum: General Help
---

### Post by Chance_O on 2008-06-09
I'm still pretty new to Linux, and have previously switched to just Ubuntu on my computer, but I would like to mound newly formatted EXT3 partitions into my home directory.  I'm a long time Windows user, and am still trying to get over the culture shock of running strictly in Linux, and have had few problems.  One that I have is that I would like to mount a few newly formatted EXT3 partitions that were previously formatted for Windows XP into my home directory.  Primarily I just reformatted an NTFS partition to EXT3, and would like to mount it as /home/chance/Backup, but I am having difficulty.  I know that the partition is /dev/sdd1, and I've edited my fstab file, but I don't think I've done so correctly.  I have two problems with this.  First, I added the following to my fstab file, 

```
# /dev/sdd1
UUID=99d24a18-86d6-45bb-82c7-666f58f5c946 /home/chance/Backup/               ext3	user	0	2
```

and it does mount, but the directory is then owned by 'root', and I cannot save files to that directory.  Also it adds the partition to my desktop as "54.9 GB Media".  I want to be able to save files to the directory, also I don't want it to display on my desktop.  What am I doing wrong?  I have several partitions I would like to setup in similar manners in my home directory.  Any help would be greatly appreciated!

---

### Post by didac on 2008-06-09
remove 'user' and make it 'defaults' or even 'users'

---

### Post by sisco311 on 2008-06-09
You also need to change the owner of the partition:
```
sudo chown -R $USERNAME. /home/chance/Backup/
```
run the command when the disk is mounted.

---

### Post by kpkeerthi on 2008-06-09
-- deleted. sisco beat me to it --

---

### Post by Chance_O on 2008-06-09
Oh my.  That all did it wonderfully!  Still recovering from years of Windows abuse, so I really appreciate the help!

---

