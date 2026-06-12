---
title: "backup partition permissions"
date: 2017-11-17
forum: General Help
---

### Post by JamButty on 2017-11-17
After wipe of 16.04 and install of 17.10, the backups prog cannot write to my backups partition. I had a similar problem before, but then root had permissions and I did not. If I am reading this right, I (max) have all permissions and root has none. (third line)
```
max@max-inspiron-384:~$ ll /media/maxtotal 208
drwxr-x---+ 3 root root   4096 Nov 17 08:39 ./
drwxr-xr-x  3 root root   4096 Nov 11 18:49 ../
drwx------  4 max  max  204800 Nov 11 17:11 Backups/


max@max-inspiron-384:~$ sudo blkid -c /dev/null -o list
[sudo] password for max: 
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/loop0 squashfs         /snap/core/3247 
/dev/loop1 squashfs         /snap/gimp/25  
/dev/loop2 squashfs         /snap/core/3440 
/dev/sda1  vfat    ESP      /boot/efi      EC12-1A71
/dev/sda2                   (not mounted)  
/dev/sda3  ntfs    OS       (not mounted)  608E3C548E3C24C6
/dev/sda4  ntfs    WINRETOOLS (not mounted) 62C87289C8725AED
/dev/sda5  ntfs    Image    (not mounted)  1C9073369073160C
/dev/sda6  ext4             /              2bfba7ca-e2ab-4503-b3c4-3ed81526da13
/dev/sda7  swap             (not mounted)  82d1c7a8-fd75-4ae9-b322-e07e781cbcd7
/dev/sda8  ext4    Backups  /media/max/Backups 69c75e7d-1011-484f-ad4b-ad1a0582acb9
max@max-inspiron-384:~$ B



```
Before I mess up all my backups, I wanted to check as I just barely understand this. Assuming I am admin (I installed and am the only user so I should be), is this what I need (UUID used is that for SDA8, the backups partition) ? adapting this from  [https://itsfoss.com/set-write-permission-ext4-partition-ubuntu-linux/](https://itsfoss.com/set-write-permission-ext4-partition-ubuntu-linux/)
```
sudo chgrp adm /media/root/69c75e7d-1011-484f-ad4b-ad1a0582acb9

sudo chmod g+w /media/root/69c75e7d-1011-484f-ad4b-ad1a0582acb9
```

---

### Post by deadflowr on 2017-11-17
fwiw adm is not an admin group, but rather a group that allows for reading/monitoring log files.
Not sure you really want to change the group to that.
I mean you can, it's just not what the group is for.

---

### Post by JamButty on 2017-11-17
I know nothing about it. I was just following the advice in the linked article. The fact that the backups program cannot write to that partition even though I have all permissions makes no sense to me.

---

### Post by deadflowr on 2017-11-17
Should it have been /media/max instead of /media/root?

---

### Post by Holger_Gehrke on 2017-11-17
On a normal Linux system 'root' can always read and write everything and everywhere. That's what being root means. Just do a 'sudo ls /media/max/Backups 69c75e7d-1011-484f-ad4b-ad1a0582acb9' from a terminal and you'll see.The problem is probably not related to root not being able to read or write the backup partition but to the configuration of your backup program. Without knowing which one you are trying to use, trying to help you is difficult.

Holger

---

### Post by JamButty on 2017-11-18
I guessed "/media/root" because "Max" already had full permissions, but as Holger_Gehrke pointed out, root should have access to everything automatically. That is what I understood and why this problem made no sense to me. I wasn't clear about the backup - it is the default Ubuntu backups program

Restores work fine, but no writes. Exact error is "Backup failed Error creating directory /media/max/Backups: Permission denied"

Aha. This is looking like a mount problem. When I query that partition normally, the system acknowledges that such a partition exist, but denies it on an "ls" command. If I invoke that partition via the standard Ubuntu files gui, then issue an "ls", suddenly it is happy.
first
> max@max-inspiron-384:~$ sudo ls /media/max/Backups
ls: cannot access '/media/max/Backups': No such file or directory

then
> max@max-inspiron-384:~$ sudo ls /media/max/Backups
autoremovelog.txt
duplicity-full.20171102T113616Z.manifest.gpg
duplicity-full.20171102T113616Z.vol100.difftar.gpg
duplicity-full.20171102T113616Z.vol101.difftar.gpg
duplicity-full.20171102T113616Z.vol102.difftar.gpg
....


So it looks like that partition is normally not mounted. the Files gui can mount it and examine files, but the backup just says "wha?"

---

### Post by JamButty on 2017-11-18
Tried the next logical step, backup (Deja Dup, I now discover) with that partition activated via the Files gui. That went a step further, revealing I had somehow knocked the last character off the computer name at some point. After correcting that and rebooting, I get:
without Files gui activation of partition - same "denied" error
with Files gui activation of partition - successful backup!

So a partial solution, but of course I should not have to separately mount the partition for Deja Dup to write to it. I never did before, so I must assume under prior Ubuntu versions Deja Dup was able to do that itself, just as the Files gui apparently does.

---

