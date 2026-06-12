---
title: "'permission denied' after moving /home directory to other drive"
date: 2016-02-08
forum: General Help
---

### Post by Nicholas_K on 2016-02-08
I was running out of space on my OS drive, so I moved my /home directory to an external drive. Since then, when I try to run any executable from that drive, I get 'Permission denied'. This is true for any executable, but my current problem is with the Dropbox daemon. (Steam is also a problem.)

Even with sudo, I get Permission denied:

```
/home  sudo ~/.dropbox-dist/dropboxd
sudo: unable to execute /home/username/.dropbox-dist/dropboxd: Permission denied
```

I infer that it isn't a file permission problem, because sudo would overcome that, but I don't know what to do to investigate the problem.

---

### Post by matt_symes on 2016-02-08
Hi

Please post the output of

```
mount | grep ^/
```

That command will show your mount points.

```
ls -l /home
```

That command will show the permission of your home folder.

Kind regards

---

### Post by yancek on 2016-02-09
What method did you use to move the directories/files?  All methods of moving/copying are not going to preserve ownership/permissions.

---

### Post by Nicholas_K on 2016-02-09
Thank you for responding. Am I wrong to assume that if it also fails using sudo, then it isn't a file permission error?

```
~  mount | grep ^/                        
/dev/sdc1 on / type ext4 (rw,relatime,discard,errors=remount-ro,data=ordered)
/dev/sde1 on /home type ext4 (rw,nosuid,nodev,noexec,relatime,data=ordered,user)
/dev/sda1 on /mnt/aba779f7-66a1-43e7-8915-3f4f1bdbd4a4 type ext4 (rw,nosuid,nodev,noexec,relatime,data=ordered,user)
/dev/sdb1 on /data type ext4 (rw,relatime,data=ordered)
/dev/sdf1 on /media/username/46F3-A5C3 type vfat (rw,nosuid,nodev,relatime,uid=1000,gid=100,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro,uhelper=udisks2)
/dev/sdd1 on /media/username/Backup type ext4 (rw,nosuid,nodev,relatime,data=ordered,uhelper=udisks2)
```

```
~  ls -l /home                            
...
drwxr-xr-x 71 root users  4096 Feb  8 21:12 username

```

```
cat /etc/fstab   
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=23e6af06-c784-48d2-b4a1-44dd96fa9972 /               ext4    discard,errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=1ace53be-f748-414d-8f3b-4c854108558a none            swap    sw              0       0
# Auto-mount data drive
UUID=2cf9c509-5029-463e-836d-d4cba1d4e3b5 /data           ext4    defaults        0       2
/dev/disk/by-uuid/aa79dde9-8b1b-4c95-a946-9aa41a8381bf /home ext4 defaults,user,comment=x-gvfs-show 0 0
/dev/disk/by-uuid/aba779f7-66a1-43e7-8915-3f4f1bdbd4a4 /mnt/aba779f7-66a1-43e7-8915-3f4f1bdbd4a4 ext4 defaults,user,comment=x-gvfs-show 0 0
```

```
cat /proc/version
Linux version 4.2.0-27-generic (buildd@lgw01-12) (gcc version 5.2.1 20151010 (Ubuntu 5.2.1-22ubuntu2) ) #32-Ubuntu SMP Fri Jan 22 04:49:08 UTC 2016
```

---

### Post by steeldriver on 2016-02-10
/home appears to be mounted with the noexec option

---

### Post by matt_symes on 2016-02-10
Hi

> **steeldriver said:**
> /home appears to be mounted with the noexec option

This is the reason why you cannot run binaries in your /home partition.

> defaults,user,comment=x-gvfs-show

Where did you get these mount options for your home directory ?

> drwxr-xr-x 71 root users  4096 Feb  8 21:12 username

Your home directory is owned by root and the groups is users. This is not right.

> What method did you use to move the directories/files? All methods of moving/copying are not going to preserve ownership/permissions. 

Agreed.

How did you move the files to the external drive ?

What guides, resources did you use ? Can you post link please so we can understand what you did.

Kind regards

---

### Post by Nicholas_K on 2016-02-16
Hello again, thank you for your help matt, yanc, and steel. I didn't follow one set of good instructions, I looked up and followed several sets of instructions, which of course were not all exactly the same. If I were to summarize it now, it would be "first move the /home dir out of the way, then mount your external drive at /home". That's basically fine but the details about the fstab file tripped me up.

Steel went straight to the issue, as matt recognized, which was the 'noexec' option for mounting that hard drive. I didn't even know that option existed, or that it was implied when I used the 'users' option, but when I added 'exec' to my fstab entry, that fixed my problem.

Thank you for the bit of education.

(Sorry I was absent on this thread for five days. I had an unrelated problem with my user account which left me unable to log in until now.)

---

### Post by sean121 on 2016-06-23
so trying to follow this thread solution as i A. cannot start my own thread yet (older user new account old account got deactivated after a long absence newer but not total noob) and this is the closest that i can find to the issue i am having. i have an older hdd with a corrupted version of 12.04 on it. the home directory is encrypted so when i have it plugged in as an external, i cannot access the files to copy them to a different drive so i can load a new distro onto the corrupted drive. i am trying to acess it through and external mount to usb on a laptop running 16.04

```
sean@sean-Presario-CQ56-Notebook-PC:~$ sudo ecryptfs-recover-private
[sudo] password for sean: 
INFO: Searching for encrypted private directories (this might take a while)...
find: &#8216;/run/user/1000/gvfs&#8217;: Permission denied
mount | grep ^/
sean@sean-Presario-CQ56-Notebook-PC:~$ mount | grep ^/
/dev/sda1 on / type ext4 (rw,relatime,errors=remount-ro,data=ordered)
/dev/sdb1 on /media/sean/d2883916-8b62-4eea-bd2d-5ef74b122d54 type ext4 (rw,nosuid,nodev,relatime,data=ordered,uhelper=udisks2)
sean@sean-Presario-CQ56-Notebook-PC:~$ ls -l /home
total 4
drwxr-xr-x 39 sean sean 4096 Jun 23 12:56 sean


```

i get about that far and then i get lost. can you point me a little more directly at the next step please?
Thanks in advance

---

