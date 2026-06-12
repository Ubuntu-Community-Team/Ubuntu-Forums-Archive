---
title: "programs can't write to fat32 partition but user can?"
date: 2006-12-07
forum: General Help
---

### Post by harty83 on 2006-12-07
I'm having an issue with my fat32 partition.  I can create files and folders via nautilus.  But if a program tries to, it gives a permissions error.  For example, if I edit a text file via gedit and try to save it, gedit returns an error that it cannot make a backup file.  Unison will not sync files that that need to be written to the fat32.  It gives 
```
Operation not permitted [chmod(/media/storage/Shared_Folder/Finances/.#Jan 2005 - Present.20061121214440.xac.135e9060a2fd2bdf2162105bc313b73f.unison.tmp)
```

Any clues on what could be causing this?  This is quite a pain!

My fat32 partition is being mounted as follows in /etc/fstab

```
UUID=4E70-A07B  /media/storage  vfat    defaults,umask=000 0       0

```

---

### Post by abarth on 2006-12-07
Are the programs nautilus and gedit running as the same user?

You can check this in a terminal by:
ps -f -C nautilus
ps -f -C gedit

Also what are the permission of the directory  /media/storage once it is mounted? Please send the output of:

ls -ld  /media/storage

A simple tool to trouble shoot write permission is the program "touch". It creates an empty file. Try:

cd /media/storage
touch empty_test_file

Does the file you want to create contains any special character? Or does a file with the same name but different capitalization already exist?

Alex

---

### Post by abarth on 2006-12-07
... oh wait! is seems that chmod failed! vfat has no file permissions. So you should be able to create a file but not to change its permissions.

---

### Post by harty83 on 2006-12-07
> **abarth said:**
> Are the programs nautilus and gedit running as the same user?

You can check this in a terminal by:
ps -f -C nautilus
ps -f -C gedit

Yes

> **abarth said:**
> 
Also what are the permission of the directory  /media/storage once it is mounted? Please send the output of:

ls -ld  /media/storage


alan@hartyslaptop:~$ ls -ld /media/storage
drwxrwxrwx 9 root root 8192 1969-12-31 19:00 /media/storage

> 
A simple tool to trouble shoot write permission is the program "touch". It creates an empty file. Try:

cd /media/storage
touch empty_test_file


Works flawlessly.

> 
Does the file you want to create contains any special character? Or does a file with the same name but different capitalization already exist?


No.  There are a bunch of files that unison wants to change the permissions for but is not allowed to as seen in the error posted before.  Gedit still returns 
```
Could not create a backup file while saving /media/storage/Shared_Folder/Cheat Sheet.txt
```
when I save it.  It does this for ANY file on the fat32 partition.

Any ideas?

Thanks!
Alan

---

### Post by harty83 on 2006-12-07
> **abarth said:**
> ... oh wait! is seems that chmod failed! vfat has no file permissions. So you should be able to create a file but not to change its permissions.

Sorry, I missed this.  So if I understand you right.  You are saying that vfat partitions do not use file permission settings so if a program tries to change permissions, it will fail?  Which means that unison is useless when used in combination with a vfat partition?

---

### Post by abarth on 2006-12-09
> **harty83 said:**
> Sorry, I missed this.  So if I understand you right.  You are saying that vfat partitions do not use file permission settings so if a program tries to change permissions, it will fail?  Which means that unison is useless when used in combination with a vfat partition?


I have installed unison to try to synchronize between a directory on a vfat and on a ext3 partition. I got an error similar to the one you got.  However, you can tell unison not to synchronize permissions:

unison -perms 0 test /media/vfat_disk/test

This will let you synchronize all your data.

---

### Post by harty83 on 2006-12-09
didn't work at first but I found an article that said to mount the vfat with the 'quiet' option in addition to the perms=0 unison option.  It now works along with gedit, etc.

Thanks!
Alan

---

### Post by ernstblaauw on 2006-12-21
Can you post your fstab? I have the same problem.

---

### Post by RyanGT on 2007-03-13
I have the exact same problem but with a slight additional twist.  I have two fat partitions that I run unison on against a linux partition and one works and the other doesn't.  The one that doesn't has these permissions and owerships when I run ls -al:
-rwxrwxrwx  1 root root   935 2007-03-12 22:21 rwkcsv.py
This is an internal partition and its fstab entry looks like this:
/dev/sda5 /mnt/RYANFAT     vfat    user,utf8,umask=000  0       0
The unison error has to do with chmod.

The fat32 partition that works fine is on a USB harddrive and its permissions and ownerships are:
-rwx------  1 ryan ryan  1684 2007-03-13 14:46 rwkcsv.py

unison has no problem with this.  So, how do I mount my internal partition in exactly the same way Ubuntu automatically mounts the USB one?  i.e. what should I put in the fstab file to make me the owner instead of root?

Thanks,

Ryan

---

