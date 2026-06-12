---
title: "mounting partitions hangs"
date: 2013-01-20
forum: General Help
---

### Post by then_dude on 2013-01-20
hello,  when i boot up ubuntu i have to skip the automatic mounting of partitions.   i  think i got this error after running the next commands  sudo e2fsck  sudo mke2fs  can anybody help me thanks

---

### Post by tgalati4 on 2013-01-21
fsck will simply check the file system.  mkfs will create (format) a file system and that could possibly overwrite data if the partition was not empty to begin with.

Post the following:

```
cat /etc/mtab
cat /etc/fstab
sudo fdisk -l
```

The last command is an L, not a number 1.

---

### Post by then_dude on 2013-01-21
thanks for your help tgalati4,  i didn't realise that the  mkfs command destroys a partition.   mmm what was i thinking? clearly not i guess... i luckily did it on an empty partition... So that was it what caused the mounting problem;   I formatted the partition, labeled it, and in the fstab file entered the new UUID and label, everything is working fine now.  thanks so much.   i was looking for badblocks on my harddisk but somebody told me to use the efsck and mkfs command... strange that i didn't check it out better...  thanks again

---

### Post by tgalati4 on 2013-01-21
```
sudo badblocks /dev/sda1
sudo fsck -cc /dev/sda1
```

The first command simply lists badblocks to the terminal.  You can output to a file using > badblocks.txt at the end of that command.  The second command runs badblocks and marks the filesystem to not use them--that is, put them in the badblock list for that partition.  You want to run badblocks on a new drive, then every so often so you can see if badblocks are increasing in time.  This would be an indication of impending drive failure.  

mkfs is the same as FORMAT in that other operating system.  So use with care.

---

### Post by then_dude on 2013-01-22
thanks tgalati4

i had piped the badblocks output to a file, so that i could store it and feed it into the file system. i didn't know  sudo fsck -cc did the same 

thanks again

---

