---
title: "Can't access files on my second fixed drive 18.04"
date: 2019-07-21
forum: General Help
---

### Post by anoldguy on 2019-07-21
Can't access files on my second fixed drive 18.04

This all started when my OCZ SSD system drive failed unexpectedly. I was on Ubuntu 16.04.
After the SSD failure, I put in a new system SSD and decided to load Ubuntu 18.04.  

I keep my data on the second drive [Ext4 v1.0] and manually mount it by clicking on it in 'Files'.  
It mounts at /media/MyUserName/MyDriveName, and I can see my files.  

Some software lets me read and modify files on MyDriveName, other software gives 'doesn't exist' or equally unhelpful error messages.  
The SNAP software works on some, but not others.


Here are the permissions:

media  drwxr-xr-x  root root

MyUserName  drwxr-xr-x+  root root

MyDriveName  drwxrwxrwx  MyUserName MyUserName

MyDocuments  drwxr-xr-x  MyUserName MyUserName 

-----------------

In addition, I have these in Home/media/MyUserName/MyDriveName

media drwxr-xr-x MyUserName MyUserName

MyUserName drwxr-xr-x MyUserName MyUserName

MyDriveName drwxr-xr-x MyUserName MyUserName

I am guessing that these are spurious and created when I was trying to use Nautilus to modify permissions.  May I just delete them?

-----------------

I have been researching and poking at this for a month and I'm just getting more confused. 

I would really not want to mount the second drive at startup, because it will change the path to my files and that's almost 500 Gigabytes that I will have to pass to my NAS [rsync] and my cloud backups.

---

### Post by TheFu on 2019-07-22
**ls -al**  of the mount point before and after the partition is mounted, please.  I'd rather not misinterpret your interpretation.  Facts are needed.

And please, use code tags so everything lines up and it easy to read.
Below is an example:
```
$ \ls -al .
total 32
drwxr-xr-x  5 root root  4096 Mar 19 16:27 .
drwxr-xr-x 31 root root  4096 Jul  4 17:57 ..
drwxr-xr-x  5 root root  4096 Jun 12 15:32 extra_stuff
drwx--x--x  2 root root  4096 Mar 19 16:41 images
drwx------  2 root root 16384 Feb 28 16:55 lost+found

$ cd extra*

$ \ls -al
total 88
drwxr-xr-x  5 root root  4096 Jun 12 15:32 .
drwxr-xr-x  5 root root  4096 Mar 19 16:27 ..
drwxr-xr-x 29 tf   tf   16384 Jun 12 15:42 ale-mail-arch
drwxr-xr-x  2 tf   tf   57344 Mar 12 21:49 tmp-photos
drwxr-xr-x  2 tf   root  4096 Jul  2 15:52 videos-tmp

```

---

### Post by anoldguy on 2019-07-22
```

myuname@NordicGarudak:~$ date
Mon Jul 22 17:30:03 EDT 2019
myuname@NordicGarudak:~$ 
myuname@NordicGarudak:~$ sudo su
[sudo] password for myuname: 
root@NordicGarudak:/home/myuname# cd /
root@NordicGarudak:/# ls -al
total 2097264
drwxr-xr-x  24 root root       4096 Jun 28 23:24 .
drwxr-xr-x  24 root root       4096 Jun 28 23:24 ..
drwxr-xr-x   2 root root       4096 Jul 18 23:47 bin
drwxr-xr-x   4 root root       4096 Jul 20 23:48 boot
drwxr-xr-x   2 root root       4096 Jun  7 16:37 cdrom
drwxr-xr-x  19 root root       4620 Jul 22 17:29 dev
drwxr-xr-x 132 root root      12288 Jul 21 18:20 etc
drwxr-xr-x   3 root root       4096 Jun  7 16:38 home
lrwxrwxrwx   1 root root         33 Jun 28 23:24 initrd.img -> boot/initrd.img-4.18.0-25-generic
lrwxrwxrwx   1 root root         33 Jun 28 23:24 initrd.img.old -> boot/initrd.img-4.18.0-24-generic
drwxr-xr-x  21 root root       4096 Jun  7 16:41 lib
drwxr-xr-x   2 root root       4096 Feb  9 19:12 lib64
drwx------   2 root root      16384 Jun  7 16:32 lost+found
drwxr-xr-x   3 root root       4096 Jun  8 10:51 media
drwxr-xr-x   3 root root       4096 Jun 11 21:26 mnt
drwxr-xr-x   3 root root       4096 Jun  8 12:38 opt
dr-xr-xr-x 287 root root          0 Jul 22 17:29 proc
drwx------   5 root root       4096 Jun 11 18:54 root
drwxr-xr-x  29 root root        840 Jul 22 17:30 run
drwxr-xr-x   2 root root      12288 Jul 10 00:30 sbin
drwxr-xr-x  18 root root       4096 Jun  8 00:57 snap
drwxr-xr-x   2 root root       4096 Feb  9 19:12 srv
-rw-------   1 root root 2147483648 Jun  7 16:32 swapfile
dr-xr-xr-x  13 root root          0 Jul 22 17:29 sys
drwxrwxrwt  16 root root       4096 Jul 22 17:30 tmp
drwxr-xr-x  10 root root       4096 Feb  9 19:12 usr
drwxr-xr-x  14 root root       4096 Feb  9 19:20 var
lrwxrwxrwx   1 root root         30 Jun 28 23:24 vmlinuz -> boot/vmlinuz-4.18.0-25-generic
lrwxrwxrwx   1 root root         30 Jun 28 23:24 vmlinuz.old -> boot/vmlinuz-4.18.0-24-generic
root@NordicGarudak:/# cd media
root@NordicGarudak:/media# ls -al
total 12
drwxr-xr-x   3 root root 4096 Jun  8 10:51 .
drwxr-xr-x  24 root root 4096 Jun 28 23:24 ..
drwxr-xr-x+  2 root root 4096 Jul 22 17:28 myuname
root@NordicGarudak:/media# cd myuname
root@NordicGarudak:/media/myuname# ls -al
total 8
drwxr-xr-x+ 2 root root 4096 Jul 22 17:28 .
drwxr-xr-x  3 root root 4096 Jun  8 10:51 ..

[Mounted Nordic2Data by clicking on it in ‘Files’]

root@NordicGarudak:/media/myuname# cd /
root@NordicGarudak:/# ls -al
total 2097264
drwxr-xr-x  24 root root       4096 Jun 28 23:24 .
drwxr-xr-x  24 root root       4096 Jun 28 23:24 ..
drwxr-xr-x   2 root root       4096 Jul 18 23:47 bin
drwxr-xr-x   4 root root       4096 Jul 20 23:48 boot
drwxr-xr-x   2 root root       4096 Jun  7 16:37 cdrom
drwxr-xr-x  19 root root       4620 Jul 22 17:29 dev
drwxr-xr-x 132 root root      12288 Jul 21 18:20 etc
drwxr-xr-x   3 root root       4096 Jun  7 16:38 home
lrwxrwxrwx   1 root root         33 Jun 28 23:24 initrd.img -> boot/initrd.img-4.18.0-25-generic
lrwxrwxrwx   1 root root         33 Jun 28 23:24 initrd.img.old -> boot/initrd.img-4.18.0-24-generic
drwxr-xr-x  21 root root       4096 Jun  7 16:41 lib
drwxr-xr-x   2 root root       4096 Feb  9 19:12 lib64
drwx------   2 root root      16384 Jun  7 16:32 lost+found
drwxr-xr-x   3 root root       4096 Jun  8 10:51 media
drwxr-xr-x   3 root root       4096 Jun 11 21:26 mnt
drwxr-xr-x   3 root root       4096 Jun  8 12:38 opt
dr-xr-xr-x 294 root root          0 Jul 22 17:29 proc
drwx------   5 root root       4096 Jun 11 18:54 root
drwxr-xr-x  29 root root        840 Jul 22 17:30 run
drwxr-xr-x   2 root root      12288 Jul 10 00:30 sbin
drwxr-xr-x  18 root root       4096 Jun  8 00:57 snap
drwxr-xr-x   2 root root       4096 Feb  9 19:12 srv
-rw-------   1 root root 2147483648 Jun  7 16:32 swapfile
dr-xr-xr-x  13 root root          0 Jul 22 17:30 sys
drwxrwxrwt  16 root root       4096 Jul 22 17:33 tmp
drwxr-xr-x  10 root root       4096 Feb  9 19:12 usr
drwxr-xr-x  14 root root       4096 Feb  9 19:20 var
lrwxrwxrwx   1 root root         30 Jun 28 23:24 vmlinuz -> boot/vmlinuz-4.18.0-25-generic
lrwxrwxrwx   1 root root         30 Jun 28 23:24 vmlinuz.old -> boot/vmlinuz-4.18.0-24-generic
root@NordicGarudak:/# cd media
root@NordicGarudak:/media# ls -al
total 12
drwxr-xr-x   3 root root 4096 Jun  8 10:51 .
drwxr-xr-x  24 root root 4096 Jun 28 23:24 ..
drwxr-xr-x+  3 root root 4096 Jul 22 17:32 myuname
root@NordicGarudak:/media# cd myuname
root@NordicGarudak:/media/myuname# ls -al
total 12
drwxr-xr-x+  3 root    root    4096 Jul 22 17:32 .
drwxr-xr-x   3 root    root    4096 Jun  8 10:51 ..
drwxrwxrwx  24 myuname myuname 4096 Jul 11 21:50 Nordic2Data
root@NordicGarudak:/media/myuname# cd Nordic2Data
root@NordicGarudak:/media/myuname/Nordic2Data# ls -al
total 4728
drwxrwxrwx  24 myuname myuname    4096 Jul 11 21:50  .
drwxr-xr-x+  3 root    root       4096 Jul 22 17:32  ..
drwxr-xr-x   2 myuname myuname    4096 Jan 31  2017  Desktop
drwxr-xr-x  35 myuname myuname    4096 Jul 14 16:02  Documents
drwxr-xr-x   8 myuname myuname   49152 Jul 21 18:43  Downloads
-rw-r--r--   1 myuname myuname    3725 Mar  4  2014  kollision.desktop
drwx------   2 root    root      16384 Jan 10  2014  lost+found
drwx------   5 myuname myuname    4096 Dec 22  2014  .Trash-1000

```

---

### Post by TheFu on 2019-07-22
```
drwxr-xr-x+  2 root root 4096 Jul 22 17:28 myuname
```
says there are ACLs on the directory.  Use getfacl to see the ACLs.
```

# ls -al
total 4728
drwxrwxrwx  24 myuname myuname    4096 Jul 11 21:50  .
drwxr-xr-x+  3 root    root       4096 Jul 22 17:32  ..
drwxr-xr-x   2 myuname myuname    4096 Jan 31  2017  Desktop
drwxr-xr-x  35 myuname myuname    4096 Jul 14 16:02  Documents
drwxr-xr-x   8 myuname myuname   49152 Jul 21 18:43  Downloads
-rw-r--r--   1 myuname myuname    3725 Mar  4  2014  kollision.desktop
```
These permissions should allow "myuname" full access.  If this really is ext4 and myuname is the correct userid.  Actually, the 777 permissions are VERY concerning on the parent directory.  I'd change that to be 755 ASAP.  777 is for lazy people who don't care about security or people who don't understand permissions at all.

So, if all at is true, you'll need to look as the restrictions on whatever snap packages happen to be used.  I don't use snaps.  Stopped the first time I had an issue like this. It was easier just to purge all those packages and install the normal apt packages instead, so I wouldn't need fight with disk access limitations that snaps enforce. 

 There is a way to modify the snap compartmentalization. I remember reading a how-to guide a few months ago about it.  Something like this:
```
sudo snap connect chromium:removable-media
```
I don't have snapd on any of my systems, do I can't test it. Sorry.

As for mounting the other disk, but not at boot, you can use autofs.  I use it for all USB connected and NFS connected storage.

---

### Post by anoldguy on 2019-07-23
Thank you TheFu, I appreciate your help.  

I’ll try this in about 24 hours when I get a chance. 

The 777 permission is my fault.  Years ago, I got frustrated with trying to access the second drive and  in desperation I found a web page that said you could use 777.

‘Disks’ says that Nordic2Data is Ext4 (version 1.0).  It’s a SATA spinning hard drive.

I’ll get rid of the SNAPs.  It sounded like a good idea, but I don’t just work in the /home directory.

I’ll also delete the /home/myuname/media, as I probably created that with my clumsy attempts.

---

### Post by TheFu on 2019-07-23
If /home/myuname/media isn't empty, I wouldn't delete it.

---

