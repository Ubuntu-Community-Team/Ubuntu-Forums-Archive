---
title: "chmod files to 777 - still can't read"
date: 2008-05-22
forum: General Help
---

### Post by hamhock on 2008-05-22
the files below reside in /media/disk - it's a NTFS partition that I create and store backup images with the program Bootit.  I had moved some of these files to /media/disk/Bootit folder, but when I ran Bootit, it could not see the files in this folder (I set folder to 777), so I moved the files back to /media/disk.  Problem is that Bootit can't see the files I moved.  It can see the files I didn't move, e.g., ubu_A6.  Why can't I see or access these files anymore from Bootit even though they are all read / write?

richard@giga1:/media/disk$ ls -l
total 9448960
drwxrwxrwx 1 root root          0 2008-05-22 18:48 Bootit
-rwxrwxrwx 1 root root 1809504256 2008-05-22 19:05 Data_6R.IMG
-rwxrwxrwx 1 root root   47320064 2008-05-21 22:18 home_A4.IMG
-rwxrwxrwx 1 root root   65197568 2008-05-22 01:02 home_A5.IMG
-rwxrwxrwx 1 root root  471036416 2008-05-22 05:46 home_A6.IMG
-rwxrwxrwx 1 root root  917123584 2008-05-20 02:48 ubu_A1.IMG
-rwxrwxrwx 1 root root 1079226880 2008-05-20 03:59 ubu_A2.IMG
-rwxrwxrwx 1 root root 1299231744 2008-05-20 19:33 ubu_A3.IMG
-rwxrwxrwx 1 root root 1306256896 2008-05-21 22:31 ubu_A4.IMG
-rwxrwxrwx 1 root root 1306114048 2008-05-22 01:02 ubu_A5.IMG
-rwxrwxrwx 1 root root 1374697984 2008-05-22 05:48 ubu_A6.IMG

---

### Post by jlacroix on 2008-05-22
Perhaps I'm misunderstanding, but did you try:

```
sudo chmod 777 -R /path/to/folder
```

And then:

```
sudo chown username -R /path/to/folder
```

I apologize if you've already tried that or if I misunderstood.

---

### Post by hamhock on 2008-05-22
> **jlacroix said:**
> Perhaps I'm misunderstanding, but did you try:

```
sudo chmod 777 -R /path/to/folder
```

And then:

```
sudo chown username -R /path/to/folder
```

I apologize if you've already tried that or if I misunderstood.

Just tried that and can't change ownership or permissions.  here's output for the disk from mount -l:

/dev/sdb1 on /media/disk type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096) []

---

### Post by hal10000 on 2008-05-22
> the files below reside in /media/disk - it's a NTFS partition that I create and store backup images with the program Bootit

are you sure you have installed the [COLOR="Red"]ntfs-3g[/COLOR] package which gives you write-access to your ntfs-patition?

sudo apt-get install ntfs-3g

---

### Post by hamhock on 2008-05-22
> **hal10000 said:**
> are you sure you have installed the [COLOR="Red"]ntfs-3g[/COLOR] package which gives you write-access to your ntfs-patition?

sudo apt-get install ntfs-3g

already installed:

ntfs-3g is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by eldragon on 2008-05-22
im not used to mounting ntfs partitions, but what effect does chmod on a ntfs partition has?

as far as i know, ntfs doesnt use the octal system separating  user / group / others like ext3 does. so what would chmodding a ntfs partition do?

*i think* you are facing the problem from the wrong angle. you should check how it is being mounted. and that you have access to that mount point (not too sure about that last part either.).

---

### Post by hamhock on 2008-05-22
> **eldragon said:**
> im not used to mounting ntfs partitions, but what effect does chmod on a ntfs partition has?

as far as i know, ntfs doesnt use the octal system separating  user / group / others like ext3 does. so what would chmodding a ntfs partition do?

*i think* you are facing the problem from the wrong angle. you should check how it is being mounted. and that you have access to that mount point (not too sure about that last part either.).

chmodding doesn't seem to have an effect.  I can create and delete files in /media/disk:
touch testfile
rm testfile

---

