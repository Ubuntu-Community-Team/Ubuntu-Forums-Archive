---
title: "issue with chmod/chown"
date: 2017-08-11
forum: General Help
---

### Post by eightermoa on 2017-08-11
Fairly new to ubuntu, I have ubuntu installed and running on a 320 gig drive and all my media files running on a seperate interal 2tb drive.  I want to change some of the properties on my media files, they are owned by root and does not let me.  I have tried using the chmod and chown commands, when I run them i do not get any error messages and I am fairly certain that I am issuing the commands correctly but it will now chown/chmod out of root. I have even tried using GKSU Nautilus and no luck.  i do not have any issues access, playing, moving, etc etc etc the files.  Do i need to chmod/chown the entire drive/partition, or what am I doing wrong?  

TIA

---

### Post by yancek on 2017-08-11
If you've been using Ubuntu for a time you know that it uses 'sudo' instead of creating a separate root user so have you used 'sudo' when trying to make these changes?  Some examples of the commands you issued and specifically what you are trying to change would be helpful.  If this is simply a data partition you could change the owner to your user but that seems overkill?  Post some examples as asked above so we have an idea of what you are trying to do.

---

### Post by TheFu on 2017-08-11
Because you already tried "GKSU Nautilus" to handle the permissions, I strongly suspect the file system isn't a native Linux one.

Which file system is the media drive using?  If it isn't a Linux/POSIX file system like ext2/3/4, zfs, xfs, jfs ... then chmod ain't gonna work.  Ok, that isn't really true, but it will never work for FAT32, FAT16, exFAT systems and getting it to work for NTFS is a bear - enough that nobody does it unless they have a corporate IT person who just loves to make things work and doesn't care that it requires 50 hours of effort to setup followed by 5 hrs a week to maintain the Windows-to-Unix userid/groupid mappings.

The **mount** command will show which file system is used.  Here's a command to remove all the not-so-interesting-mounts and leave those for normal disks.
 
```
$ mount |egrep '[shv]d[a-z]|mapper'
/dev/mapper/istar--vg-root on / type ext4 (rw,errors=remount-ro)
/dev/sda2 on /boot type ext2 (rw)
/dev/mapper/istar--stuff-lv--tv on /TV type ext4 (rw,errors=remount-ro)
/dev/mapper/istar--vg2-lv_media2 on /DD type ext4 (rw,errors=remount-ro)
/dev/mapper/istar--vg-lv_media on /D type ext4 (rw,errors=remount-ro)
/dev/sdf1 on /misc/2TB type ext4 (rw,nosuid,nodev)
/dev/sdd2 on /misc/b-3.5T type ext4 (rw,nosuid,nodev)
/dev/mapper/istar--8TB-istar--back3--a on /misc/b-D3 type ext4 (rw,nosuid,nodev)
/dev/mapper/istar--8TB-istar--back3--b on /misc/b-D4 type ext4 (rw,nosuid,nodev)
/dev/mapper/istar--vg2--back-lv_media2_back on /misc/b-DD type ext4 (rw,nosuid,nodev)
```

So you can see that I use ext4 and don't have any NTFS or exfat/fat32 mounts on my media 

If you like, you can just run **mount** and manually remove all the pseudo-file systems yourself.

There are probably easier ways. They just didn't come to me this morning.

With NTFS, you can control the owner and group using the mount options. I'll wait for your confirmation on the file system type involved.  You can search for "ubuntu mount ntfs owner" to fined a how-to guide.

---

### Post by SeijiSensei on 2017-08-11
Grant read permission to all users on all files under /media/myfiles

```

cd /media
sudo chmod a+r -R myfiles

```

Write privileges should be limited to an administrative user like you.  One option is to put all the media files into your group and grant that group write permissions.  Suppose that user is named "beverly."  Every Ubuntu user has a group of the same name (see /etc/group), so we can use:

```

cd /media
sudo chown -R root:beverly myfiles
sudo chmod -R g+w myfiles

```

Now members of the "beverly" group can write and delete files in /media/myfiles. The "sudo" is obviously important as is the "-R" (recurse) switch.  Without it the changes are only made in the local directory.  You need -R to apply the changes to all the files below that directory as well.

---

### Post by eightermoa on 2017-08-11
> **TheFu said:**
> Because you already tried "GKSU Nautilus" to handle the permissions, I strongly suspect the file system isn't a native Linux one.

Which file system is the media drive using?  If it isn't a Linux/POSIX file system like ext2/3/4, zfs, xfs, jfs ... then chmod ain't gonna work.  Ok, that isn't really true, but it will never work for FAT32, FAT16, exFAT systems and getting it to work for NTFS is a bear - enough that nobody does it unless they have a corporate IT person who just loves to make things work and doesn't care that it requires 50 hours of effort to setup followed by 5 hrs a week to maintain the Windows-to-Unix userid/groupid mappings.

The **mount** command will show which file system is used.  Here's a command to remove all the not-so-interesting-mounts and leave those for normal disks.
 
```
$ mount |egrep '[shv]d[a-z]|mapper'
/dev/mapper/istar--vg-root on / type ext4 (rw,errors=remount-ro)
/dev/sda2 on /boot type ext2 (rw)
/dev/mapper/istar--stuff-lv--tv on /TV type ext4 (rw,errors=remount-ro)
/dev/mapper/istar--vg2-lv_media2 on /DD type ext4 (rw,errors=remount-ro)
/dev/mapper/istar--vg-lv_media on /D type ext4 (rw,errors=remount-ro)
/dev/sdf1 on /misc/2TB type ext4 (rw,nosuid,nodev)
/dev/sdd2 on /misc/b-3.5T type ext4 (rw,nosuid,nodev)
/dev/mapper/istar--8TB-istar--back3--a on /misc/b-D3 type ext4 (rw,nosuid,nodev)
/dev/mapper/istar--8TB-istar--back3--b on /misc/b-D4 type ext4 (rw,nosuid,nodev)
/dev/mapper/istar--vg2--back-lv_media2_back on /misc/b-DD type ext4 (rw,nosuid,nodev)
```

So you can see that I use ext4 and don't have any NTFS or exfat/fat32 mounts on my media 

If you like, you can just run **mount** and manually remove all the pseudo-file systems yourself.

There are probably easier ways. They just didn't come to me this morning.

With NTFS, you can control the owner and group using the mount options. I'll wait for your confirmation on the file system type involved.  You can search for "ubuntu mount ntfs owner" to fined a how-to guide.


Thanks for the reply.  I forgot to add a few things (its been well over 100 degree and i have been working outside 16+ hours a day for the last week).  I am running a dual boot Ubuntu 16.04 (i know there isnt a difference between "server" and (pardon my ignorance) desktop version when it comes to file system, just whats installed from the get go, according to what I have read, if I am wrong please correct me) "desktop version" and windows 7.  The installation went off without a hitch.  I put the files on my second hard drive via windows and it is NTFS.  But I am noticing a lot of ubuntu programs crashing repeatedly (nautilus, sudo, etc) so I wonder if I have a hardware problem or it doesnt like my build (about 11 years old).  So I am going to pull the media off my drive (ETA 3 hours), format it to EXT3 and retry.  know about good programs that will allow me to see the drive in windows that wont screw anything up?

TheFu and Seiji, thanks for the reply and feedback, I will try your suggestions of this doesnt work.

Thanks all, great group here!!

---

### Post by TheFu on 2017-08-11
If you are going to reformat, don't use EXT3.  Use EXT4. There are reasons.

If you need Windows to have access, then there isn't much choice - stay NTFS.  You can leave it as NTFS, but you'll need to control the permissions in the mount, not after the fact.  I already provided the search terms.

---

### Post by eightermoa on 2017-08-11
> **TheFu said:**
> If you are going to reformat, don't use EXT3.  Use EXT4. There are reasons.

If you need Windows to have access, then there isn't much choice - stay NTFS.  You can leave it as NTFS, but you'll need to control the permissions in the mount, not after the fact.  I already provided the search terms.


lol i moved those files to my hard drive that has ubuntu OS on it and it showed me as the ownership, I formatted my other drive using gparted to ext4 and it shows root as the owner, tried chmod/chown and the commands didnt fail but it didnt do anything, and I can not write to that drive ](*,).  

here is the result of [COLOR=#000000][FONT=&amp]mount |egrep '[shv]d[a-z]|mapper'[/FONT][/COLOR]

/dev/sda5 on / type ext4 (rw,relatime,errors=remount-ro,data=ordered)

---

### Post by TheFu on 2017-08-12
If you want help with the permissions, post the **ls -al** for the mount point directory.

In Unix, commands that work don't output anything.  It is only when there is an error that the failure is output.  However, if your command doesn't truly ask for what is desired and there is not an error, then nothing will be output.  This is one of the differences in the Unix philosophy when compared to other OSes.

---

### Post by eightermoa on 2017-08-12
> **TheFu said:**
> If you want help with the permissions, post the **ls -al** for the mount point directory.

In Unix, commands that work don't output anything.  It is only when there is an error that the failure is output.  However, if your command doesn't truly ask for what is desired and there is not an error, then nothing will be output.  This is one of the differences in the Unix philosophy when compared to other OSes.

Yep.  I am starting to learn that.  I replaced my hard drive with a new one to see if it would fix my crashing problem, so far so good. 

I notice when I format with gparted, it locks the drive rights to admin, when I right click on the drive and format it that way, it gives me rights, dont know if that helps.

```
eightermoa@eightermoa-nForce-750i-SLI://$ ls -al
total 108
drwxr-xr-x  24 root root  4096 Aug 11 23:43 .
drwxr-xr-x  24 root root  4096 Aug 11 23:43 ..
drwxr-xr-x   2 root root  4096 Aug 11 21:43 bin
drwxr-xr-x   3 root root  4096 Aug 11 23:44 boot
drwxr-xr-x   2 root root  4096 Aug 11 21:37 cdrom
drwxr-xr-x  19 root root  4340 Aug 12 07:15 dev
drwxr-xr-x 133 root root 12288 Aug 11 23:43 etc
drwxr-xr-x   3 root root  4096 Aug 11 21:38 home
lrwxrwxrwx   1 root root    33 Aug 11 23:43 initrd.img -> boot/initrd.img-4.10.0-32-generic
lrwxrwxrwx   1 root root    33 Aug 11 21:39 initrd.img.old -> boot/initrd.img-4.10.0-28-generic
drwxr-xr-x  22 root root  4096 Aug 11 21:43 lib
drwxr-xr-x   2 root root  4096 Aug  1 04:19 lib64
drwx------   2 root root 16384 Aug 11 21:35 lost+found
drwxr-xr-x   3 root root  4096 Aug 11 23:43 media
drwxr-xr-x   2 root root  4096 Aug  1 04:17 mnt
drwxr-xr-x   2 root root  4096 Aug  1 04:17 opt
dr-xr-xr-x 238 root root     0 Aug 12 06:57 proc
drwx------   4 root root  4096 Aug 11 23:36 root
drwxr-xr-x  24 root root   780 Aug 12 07:04 run
drwxr-xr-x   2 root root 12288 Aug 11 21:47 sbin
drwxr-xr-x   2 root root  4096 Apr 29 01:38 snap
drwxr-xr-x   2 root root  4096 Aug  1 04:17 srv
dr-xr-xr-x  13 root root     0 Aug 12 06:57 sys
drwxrwxrwt  11 root root  4096 Aug 12 07:16 tmp
drwxr-xr-x  11 root root  4096 Aug  1 04:24 usr
drwxr-xr-x  14 root root  4096 Aug  1 04:34 var
lrwxrwxrwx   1 root root    30 Aug 11 23:43 vmlinuz -> boot/vmlinuz-4.10.0-32-generic
lrwxrwxrwx   1 root root    30 Aug 11 21:39 vmlinuz.old -> boot/vmlinuz-4.10.0-28-generic
```

---

### Post by TheFu on 2017-08-12
please,. please, please please, use "code tags" - too hard to read otherwise.  *Advanced Reply* # button.

Why are you showing / ?  That isn't where the new disk is mounted and doesn't show the permissions for the directory with the files.

If you have:
```
$ df -h
Filesystem                         Size  Used Avail Use% Mounted on
/dev/sda5                           20G  3.9G   15G  22% /
/dev/mapper/vg--hadar-lv--hadar    388G  120G  248G  33% /var
/dev/mapper/vg--hadar-lv--backups  387G  265G  103G  73% /Backups 
romulus:/raid/media                1.8T  1.7T   57G  97% /R 
``` 
and permissions on /R is the issue, then I want to see:
```
$ ls -al /R
total 80
drwxrwsr-x  7 thefu   media    4096 May 21 11:51 ./
```

So ... I own the mount point and can change the permissions without sudo.  The *media* group can write to it and any files or directories created under the /R/ directory will have the "media" group by default (the g+s does that) and *other* has read-only access. "other" means anyone NOT either *thefu* or in the *media* group.  BTW, permissions here don't matter if it is local or remote since I use NFS.  Having a media group is handy when running media players on the network, like Kodi or Plex.

You can also see that my / partition barely has anything in it and it isn't very large.  OTOH, the machine I'm showing doesn't have any GUI, so all the bloated GUI stuff isn't loaded.  However, my primary desktop doesn't have much local storage either.  Just checked and it is using 14G out of 17G allocated for / - which includes everything.  I keep large files on NFS storage, not local.

---

### Post by eightermoa on 2017-08-12
ok sorry!!

I dont know what it did what it did.  I just ran the command that you mentioned.  :-)

df -h

```
Filesystem      Size  Used Avail Use% Mounted on
udev            2.0G     0  2.0G   0% /dev
tmpfs           395M  6.3M  389M   2% /run
/dev/sda1       290G  4.6G  271G   2% /
tmpfs           2.0G  280K  2.0G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           2.0G     0  2.0G   0% /sys/fs/cgroup
tmpfs           395M   60K  395M   1% /run/user/1000
/dev/sdb1       1.8T   68M  1.7T   1% /media/eightermoa/storage
```


```
ls -al /media/eightermoa/storage
total 24
drwx------  3 eightermoa eightermoa  4096 Aug 12 13:49 .
drwxr-x---+ 3 root       root        4096 Aug 12 07:21 ..
drwx------  2 root       root       16384 Aug 12 07:18 lost+found
```

I hope the above is what you asked for.  I will explain my exact steps if that helps

downloaded ubuntu desktop from ubuntus website, used ubuntu to extract the iso file to my flash drive, booted to my flashdrive, clicked "try ubuntu", went in with gdisk and wiped all my partitions and everything, formated both drives to ext4, installed ubuntu, did all my updates/upgrades/dist-upgrades, my 1.8tb drive on /dev/sdb1 was owned by room, did sudo chmod/chown to the drive, the partition and nothing, so opened the drive, right clicked on the drive from the menu tree on the left, formated it again to ext4 and now i own it.  hopefully that helps

---

### Post by TheFu on 2017-08-12
Exactly, what **chown** and **chmod** commands did you run?

Did you run **mkfs**?
Did you run **mount**?

Also, you showed sda5 previously (post #7), but now you are showing sda1 and sdb1.  Huh?  I'm lost. Things aren't consistent.

---

### Post by eightermoa on 2017-08-12
> **TheFu said:**
> Exactly, what **chown** and **chmod** commands did you run?

Did you run **mkfs**?
Did you run **mount**?

Also, you showed sda5 previously (post #7), but now you are showing sda1 and sdb1.  Huh?  I'm lost. Things aren't consistent.

lol you should see how lost I am LOL

sorry for the confusion.  When i posted post #7, I was running a 320 gig that had a dual boot with windows 7 and ubuntu.  I replaced that hard drive last night with another 320 (i think the disc was TU) and reinstalled ubuntu on it but this time i JUST put ubuntu on, no windows 7 dual boot, maybe thinking (but highly unlikely) that the dual boot was screwing stuff up.

I did not roun mkfs or any mount commands, I went to the search your computer thing, typed in disks and mounted it that way, didnt change any options when i mounted it just clicked mount and ok (which i am assuing is wrong).

the commands I ran:
```

sudo chown -R eightermoa /dev/sdb
sudo chmod ugo+wx /media/eightermoa/698052c2-c360-4c8b-9c1a-87f7bbe7c12e
```

why does gparted format and lock it to root and when i do it the other way (right click on the drive in the explorer and click format) it owns it to me?

---

### Post by TheFu on 2017-08-12
We were all new at some point.

Running commands with sudo that you don't understand is VERY DANGEROUS.

That chown is bad - like I'd start over "bad."  Never run a chown on a disk device like that.  chown and chmod only work on mounted file systems (directories and files).

That chmod command isn't so bad, but not very useful.  You didn't provide "READ" access to anyone.  If you want a userid or group or "other" to have read access, then the permissions need to have that.

To save yourself confusion and frustration, my best advice  is that you work through a Unix permissions tutorial (google "unix file permission tutor").  That should take about 45 minutes, tops.  Most tutorials don't cover more than the basics, but that should be enough for the next 6 months.  

On your calendar, make a reminder 6 months from now to come back to learn all the permissions - there are about 4K different possible settings, but there are really just 4 groups of permissions with the specific settings for each group (just 8 really) repeating for each of the 4 groups. That means once you learn 8 permissions, you know them all, sorta. ;)

Ok - enough lecturing.  Time for solutions. ;)

[LIST=1]
[*]un-mount the drive. - ```
sudo umount /media/eightermoa/698052c2-c360-4c8b-9c1a-87f7bbe7c12e
``` NEVER format or partition a mounted drive.
[*]create a new ext4 file system on the device. - ```
sudo mkfs -t ext4 /dev/sdb1
```   sdb is the entire drive.  sdb1 is the first partition inside the drive (which I assume you create somehow).
[*]create an empty directory to mount this new file system onto.  That is called "a mount point" - it is just an empty directory.  ```
sudo mkdir -p /D/media
```
[*]mount the new file system onto /D/media.  ```
sudo mount -t ext4  /dev/sdb1 /D/media
``` check that the mount is working using df.  ```
df -h
``` That should show that /dev/sdb1 is mounted to /D/media.  All good?
[*] fix the owner and group for the new storage.  ```
sudo chown -R  eightermoa:eightermoa /D/media
```
[*] make a few different media directories, as required by kodi, plex, and most other media servers.  ```
cd /D/media ; mkdir Music Movies TV Photos; chmod 775 Music Movies TV Photos
``` See how we didn't need sudo for that?
[*] Lastly, let's force all new files and subdirectories to use the same group, automatically in the future.  ```
chmod g+s Music Movies TV Photos
```
[/LIST]

If you want to mount this storage through the fstab - and you should - then [https://help.ubuntu.com/community/AutomaticallyMountPartitions#Systemwide_Mounts](https://help.ubuntu.com/community/AutomaticallyMountPartitions#Systemwide_Mounts) has what you want.  Basically, it comes down to 3 steps.
a) determine the UUID for the specific partition (sdb1) that you want to mount - use blkid for that.
b) open the fstab using **sudoedit /etc/fstab** (using sudoedit is the safest way to edit system files). Copy an existing line in the /etc/fstab that is working, using ext4, and modify the UUID, "mount point" and change the last field from 1 --> 2.  Multiple spaces are the same as 1 space. Be certain to keep the exact number of fields, as separated by spaces.  Mistakes in the fstab are bad - like your system won't boot "bad".  Any line that begins with a #, is a comment. That is a common thing across almost every text file on a Unix system.
c) Assuming the fstab is edited correctly, run **sudo mount -a** This will read the fstab and mount any devices specified inside there as the options request.  Already mounted storage will be left alone. If you **umount** (there isn't an 'n' in the command) the sdb1 storage (either the /dev/sdb1 or path to the file can be used or any of the other links under /dev/mapper or /dev/disk/by- ... can be used). Don't worry about those other places for disk links now.

That should be it.  If I didn't make any mistakes or you don't see them and fix them. ;)

You should look up every command above, learn to read the man pages for each, to solidify knowledge.  **man mount** will show the manual for the mount command, for example.

---

### Post by eightermoa on 2017-08-14
wow man thank you for taking the time to write that book!!!  Let me get started and I will get back to you!!!

---

### Post by TheFu on 2017-08-14
> **eightermoa said:**
> wow man thank you for taking the time to write that book!!!  Let me get started and I will get back to you!!!

If you hadn't posted the exact commands (which didn't work and were bad), I wouldn't have known what you knew and didn't know. That was very helpful. Much of this stuff isn't intuitively obvious, until someone tells you.  Eventually, things "just click" and it all makes sense.


Ok, and I type over 50 wpm, easily - perhaps over 80wpm. ;)

---

### Post by eightermoa on 2017-08-14
Sweet, I clocked mine at 82 a week ago.  and I ran everything you said and it went off without a hitch.  So thank you!!.  I will read up on the commands.  I work on cisco stuff a lot for work but not a lot on the command line stuff so this is why I am trying to get this working at home.

Got time for another question?? ;-)

---

### Post by eightermoa on 2017-08-16
The only issue I am having, when i restart my PC it doesnt keep the media mounted to D, how do you do it to where it auto mounts it?

---

### Post by eightermoa on 2017-09-03
well after some reading i figured it out, edited my fstab and added:

```
# Automount of /D
UUID=ab59dd0a-3128-484b-a3d0-fcfdff756b51 /D/media ext4 errors=remount-ro 0 1
```

restarted and it work!!!  Thanks!!

---

