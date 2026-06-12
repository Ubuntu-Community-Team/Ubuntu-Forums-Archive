---
title: "No disk space left --- But df tells me it's NOT true"
date: 2008-07-01
forum: General Help
---

### Post by kung fu buntu on 2008-07-01
I was trying to check out some source code and svn blocks... In parallel I try to take a note in Zim and it tells me there is no space left in the system.

I re-check my system:
```
df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              16G   15G  545M  97% /
tmpfs                1007M     0 1007M   0% /lib/init/rw
udev                   10M   88K   10M   1% /dev
tmpfs                1007M     0 1007M   0% /dev/shm
/dev/sdb1             307G  295G  9.0G  98% /vault
/dev/sdb2             160G   56G  102G  36% /xvault

```

I know that 5% of the space is reserved, but I think I've set that to 1%. BTW, how can I check its value?

Another thing is that I just moved 5GB to another drive (from sdb1 to sdb2, and ended with 9GB free)... but that didn't solve anything.

I also made a "brute" reboot to force fsck at reboot, but that didn't help.

What is wrong? How can I fix this? Are the pinguins on drugs?

I remember something weird more or less like this happenned in the past, in which my free space changed after the filesystem was checked.



EDIT: it seems the e2fsck at system boot is not enough. I will run it in single user mode and see what happens.
I also have enough i-nodes left (df -i).

---

### Post by kung fu buntu on 2008-07-01
Damn it...


I'm out of inodes... (I should have **df -i** when I got the error message and not after deleting the svn files).


The thing that sucks the most is that there is no way to increase this...
LINUX I HATE YOU! Always giving me headaches :cry:

---

### Post by benfindlay on 2008-07-01
Just a side thought, have you cleaned out your temporary installation cache? That might free up a little space for you!

Hope this helps!

---

### Post by drs305 on 2008-07-01
As benfindlay suggested, you can clean out your /var/cache/apt/archives of downloaded packages with:
```
sudo aptitude clean
```

I also suspect you have some old trash taking up space. Run the following command to find all the Trash folders on your main partition:
```

sudo find / -type d -iname Trash
```

You can then look at them and delete the appropriate Trash/files entries with:
```
gksudo nautilus
```

---

### Post by benfindlay on 2008-07-01
This has just occured to me: will sudo apt-get clean do the same as sudo aptitude clean or does it depend which installation method you've used for specific packages. I.e., if I have used both for installation, would I have to run both cleans to get rid of everything?

---

### Post by drs305 on 2008-07-01
> **benfindlay said:**
> This has just occured to me: will sudo apt-get clean do the same as sudo aptitude clean or does it depend which installation method you've used for specific packages. I.e., if I have used both for installation, would I have to run both cleans to get rid of everything?

It does the same thing. Either will clean out /var/cache/apt/archives . They may still store their information in different folders in /var/lib, but whether a package is installed via aptitude or apt-get the information is also registered in /var/lib/dpkg/info

To test this, I installed 2 small packages - one with aptitude and another with apt-get. Then I purged them using the other app and both were cleanly removed.

---

### Post by kung fu buntu on 2008-07-01
I do apt-get clean once in a while.

The problem is my inodes number :(
I dont know what I did (because I was working on another partition) but... I'm out of inodes now!!!!!!!!!!


Is there a way to get statistics for inode usage in a hierarchy?
Similar to kdirstat for disk usage.

I need to find where most inodes are being used in order to move or delete or burn the files away.

EDIT: nevermind... inode refers to the number of files (IIRC there is 1 inode for every 4KB chunks). And kdirstat already shows the number of files. Still... if there is a better way please share it.

---

### Post by Habbit on 2008-07-01
It's very very strange to run out of inodes nowadays (my most used partition has 16% of inodes used). If it's on your root partition, try deleting temporary files that could have accumulated from use.

If you run into this problem on a data partition, which can be more probable if it's used for development or other tasks which involve lots of small files, you need to back the data up and mkfs the partition anew, with either:
[LIST]
[*]A filesystem with dynamic inodes, which thus won't run out of them, like ReiserFS.
[*]The same filesystem (I'm assuming ext3 here) with more inodes. The defaults for mkfs.ext3 create one inode per 16 KiB, but supplying the "-T news" option to mkfs will create four times as many - you can see the effects of the -T options in the mke2fs man page and the available settings profiles in /etc/mke2fs.conf.
[/LIST]

Be careful to back everything up correctly. For a data partition, I'd suggest "tar -cpjf /other/partition/backup.tar.bz2 ." from the mount point of the partition you want to back up. For a system partition, booting from a LiveCD may be necessary.

---

