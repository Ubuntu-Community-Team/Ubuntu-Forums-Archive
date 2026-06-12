---
title: "Some folders are locked... Why? and how to remove it?"
date: 2008-05-06
forum: General Help
---

### Post by Kdar on 2008-05-06
For some reason.. Some folders on my external (FAT32) are locked.. I can't remove it, or rename files inside of it.

I never ask it to be locked.. How do I un-lock it?

---

### Post by tamoneya on 2008-05-06
that is probably because they are currently owned by the root user.  To fix this you need to change the owner to you.```
chown -R username /path/to/my/directory/
``` The -R makes it recursive and therefore all sub-directories will also change owners.

---

### Post by aysiu on 2008-05-06
Only *some* of them are locked? That's odd. Can you paste these commands in [the terminal](http://www.psychocats.net/ubuntu/terminal) and then paste the output back here? ```
sudo fdisk -l
df -h
```

By the way, *chown* and *chmod* do not work on FAT32 and NTFS partitions.

---

### Post by Kdar on 2008-05-06
Here

```
kdar@kdar-desktop:~$ sudo fdisk -l
[sudo] password for kdar: 

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00a900a9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sda2           12749       23845    89136652+  83  Linux
/dev/sda3           23846       24321     3823470   82  Linux swap / Solaris
d
Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f9c798a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    c  W95 FAT32 (LBA)
kdar@kdar-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              85G  7.4G   73G  10% /
varrun               1013M  100K 1013M   1% /var/run
varlock              1013M     0 1013M   0% /var/lock
udev                 1013M   68K 1013M   1% /dev
devshm               1013M   12K 1013M   1% /dev/shm
lrm                  1013M   38M  976M   4% /lib/modules/2.6.24-16-generic/volatile
gvfs-fuse-daemon       85G  7.4G   73G  10% /home/kdar/.gvfs
/dev/sdb1             233G  132G  102G  57% /media/My Book
kdar@kdar-desktop:~$ 

```

Yes.. Only some.. Like my Photos folder.. and my Music folder for some reason..

But everything else is ok....

---

### Post by aysiu on 2008-05-06
Can you try pasting these commands in ```
sudo umount /dev/sdb1
sudo mount -t vfat /dev/sdb1 /media/My\ Book -o iocharset=utf8,umask=000
``` and then trying again to see if they're locked?

---

### Post by Tiede on 2008-05-06
Some of my windows folders are locked as well. That just happens to be the /Windows directory, the /Program Files and a few other system files/directories.
Also, I had a problem with automatically generated user folders being locked (i.e, My Pictures, My Videos et al.). I think it is a safeguard against modifying these files by accident and never looked into it. Maybe the files are reported read-only on the disk and ubuntu shows them as locked as a result.
My disk is also a FAT32 partition.
Yours is an external drive though, so I am a little curious as o which folders are locked. Do you use this on windows as well? If so, check if windows is not setting the folders as read-only in their properties window.

---

### Post by Kdar on 2008-05-06
Here is what I get when I try to run second code
```
kdar@kdar-desktop:~$ sudo mount -t vfat /dev/sdb1 /media/My\ Book -o iocharset=utf8,umask=000
mount: mount point /media/My Book does not exist

```

---

### Post by aysiu on 2008-05-06
> **Kdar said:**
> Here is what I get when I try to run second code
```
kdar@kdar-desktop:~$ sudo mount -t vfat /dev/sdb1 /media/My\ Book -o iocharset=utf8,umask=000
mount: mount point /media/My Book does not exist

```
That's weird. I guess the /media/My Book mount point must be dynamically created. That's okay. We'll create a static one, then: ```
sudo mkdir /media/My\ Book
sudo mount -t vfat /dev/sdb1 /media/My\ Book -o iocharset=utf8,umask=000
```

---

### Post by ejay563 on 2008-05-06
After the disk automatically mounts, take note of where it mounts, and do 

```
$ sudo chmod -r 777 /path/to/disk

```

That will set all the directories to readable/writable to all users and user types.

---

### Post by aysiu on 2008-05-06
> **ejay563 said:**
> After the disk automatically mounts, take note of where it mounts, and do 

```
$ sudo chmod -r 777 /path/to/disk

```

That will set all the directories to readable/writable to all users and user types.
In my three years of using Ubuntu, I've never seen *chmod* work on a FAT32 drive.

---

### Post by ejay563 on 2008-05-06
> **aysiu said:**
> In my three years of using Ubuntu, I've never seen *chmod* work on a FAT32 drive.
Wierd. I'm almost positive I've used it, and it worked fine. I guess we'll find out...

---

### Post by adept_king on 2008-08-13
I can attest to the apparent fact that chmod and chown commands aren't working on my fat32 drive.

moreover,
Why is it that whenever i copy a folder from my own DVD ROM backups, locked files are being made?  

Is this some kind of security feature that I could just as well disable?

---

### Post by jerome1232 on 2008-08-13
That dvd copies are just because they retain their read-only attribute, those one you can chmod

```
chmod -u+w <files-that-need-to-be-changed>
```'

edit: I originally wrote my chmod command wrong, while it would work, it would give anybody write access to your files, I have fixed it. (-u instead of -o)

---

### Post by bodhi.zazen on 2008-08-13
> **adept_king said:**
> I can attest to the apparent fact that chmod and chown commands aren't working on my fat32 drive.[code]

No they do not. You set ownership and permissions of FAT and NTFS file systems as a part of the mounting process in /etc/fstab.

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131") 

[quote]moreover,
Why is it that whenever i copy a folder from my own DVD ROM backups, locked files are being made?  

Is this some kind of security feature that I could just as well disable?

Once the files are copied (moved) to a Linux native file system, you can then chown / chmod at will.

[uhelp]community/FilePermissions[/uhelp]

---

### Post by chrisccoulson on 2008-08-13
Yes, chown and chmod definately do not work *properly* on FAT32/NTFS volumes, as they do not support Linux file permissions. However, the reason you may see only *some* folders/files locked on a FAT32 volume is because their read-only attribute is set. I have this problem all the time when transferring files between my work PC (Windows) and my home PC (Ubuntu) using my FAT32 USB stick.

You can use Nautilus to change the read-only attribute. chmod will also change the read-only attribute by toggling the write ('w') flag. You can't change the read ('r') or execute ('x') flags using chmod (they may appear to change but will be forgotten if you unmount and then remount the volume), and you cannot change the ownership of files on FAT32 volumes using chown at all.

---

### Post by mc4man on 2008-08-13
> In my three years of using Ubuntu, I've never seen chmod work on a FAT32 drive.
> Wierd. I'm almost positive I've used it, and it worked fine. I guess we'll find out... 
In terms of Hardy

You can certainly use chomd on a FAT or FAT32 partition whether on an internal drive or 'true' removable like a usb flash and the change is persistent across Os's and other pc's (in the case of usb.

As far as locked files on a windows partition or on files transferred from windows to a usb drive i don't see that as possible in xp home or any vista home editions, maybe on xp pro, vista business.

---

### Post by aysiu on 2008-08-14
You can't *chown* NTFS or FAT: ```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.1"
ubuntu@ubuntu:~$ ls -l /media/fat16/
total 0
-rwxr-xr-x 1 root root 0 2008-08-15 00:57 testfat.txt
ubuntu@ubuntu:~$ sudo chown -R ubuntu:ubuntu /media/fat16
chown: changing ownership of `/media/fat16/testfat.txt': Operation not permitted
chown: changing ownership of `/media/fat16': Operation not permitted
ubuntu@ubuntu:~$ ls -l /media/fat16/
total 0
-rwxr-xr-x 1 root root 0 2008-08-15 00:57 testfat.txt
ubuntu@ubuntu:~$ ls -l /media/ntfs/
total 0
-rwxrwxrwx 1 root root 0 2008-08-15 00:57 testntfs.txt
ubuntu@ubuntu:~$ sudo chown -R ubuntu:ubuntu /media/ntfs
ubuntu@ubuntu:~$ ls -l /media/ntfs/
total 0
-rwxrwxrwx 1 root root 0 2008-08-15 00:57 testntfs.txt
ubuntu@ubuntu:~$ ls -l /media/ext3/
total 12
drwx------ 2 root root 12288 2008-08-15 00:55 lost+found
-rw-r--r-- 1 root root     0 2008-08-15 00:57 testext3.txt
ubuntu@ubuntu:~$ sudo chown -R ubuntu:ubuntu /media/ext3
ubuntu@ubuntu:~$ ls -l /media/ext3/
total 12
drwx------ 2 ubuntu ubuntu 12288 2008-08-15 00:55 lost+found
-rw-r--r-- 1 ubuntu ubuntu     0 2008-08-15 00:57 testext3.txt
ubuntu@ubuntu:~$
``` and you can't *chmod* FAT or NTFS either: ```
ubuntu@ubuntu:~$ ls -l /media/ntfs
total 0
-rwxrwxrwx 1 root root 0 2008-08-15 01:07 testntfs.txt
ubuntu@ubuntu:~$ sudo chmod 755 /media/ntfs/testntfs.txt
ubuntu@ubuntu:~$ ls -l /media/ntfs
total 0
-rwxrwxrwx 1 root root 0 2008-08-15 01:07 testntfs.txt
ubuntu@ubuntu:~$ ls -l /media/fat16
total 0
-rwxr-xr-x 1 root root 0 2008-08-15 01:07 testfat.txt
ubuntu@ubuntu:~$ sudo chmod 777 /media/fat16/testfat.txt
ubuntu@ubuntu:~$ ls -l /media/fat16
total 0
-rwxr-xr-x 1 root root 0 2008-08-15 01:07 testfat.txt
ubuntu@ubuntu:~$ ls -l /media/ext3
total 12
drwx------ 2 ubuntu ubuntu 12288 2008-08-15 00:55 lost+found
-rw------- 1 ubuntu ubuntu     0 2008-08-15 00:57 testext3.txt
ubuntu@ubuntu:~$ sudo chmod 777 /media/ext3/testext3.txt
ubuntu@ubuntu:~$ ls -l /media/ext3
total 12
drwx------ 2 ubuntu ubuntu 12288 2008-08-15 00:55 lost+found
-rwxrwxrwx 1 ubuntu ubuntu     0 2008-08-15 00:57 testext3.txt
ubuntu@ubuntu:~$
``` The output is from 8.04 (Hardy Heron).

---

### Post by mc4man on 2008-08-15
> and you can't chmod FAT or NTFS either:
Maybe we're talking about 2 diff. things anyway ....
NTFS is a moot point ,it mounts with full permission and any read only files are unlocked. In the case of fat or fat32 chomd does work

Ex. fat32 partition - file attribute set as read only in windows

> doug@doug-desktop:~$ ls -l /media/FILES
total 24
drwx------ 2 doug root 8192 2008-08-14 22:55 New Folder
drwx------ 4 doug root 8192 2008-08-14 20:48 PATCHES
-r-x------ 1 doug root   17 2008-08-13 20:05 test.txt 
doug@doug-desktop:~$ chmod u+rw -R /media/FILES
doug@doug-desktop:~$ ls -l /media/FILES
total 24
drwx------ 2 doug root 8192 2008-08-14 22:55 New Folder
drwx------ 4 doug root 8192 2008-08-14 20:48 PATCHES
-rwx------ 1 doug root   17 2008-08-13 20:05 test.txt
doug@doug-desktop:~$ 


A fat or fat32 usb flash drive is the same, files set as read only in windows will be changed. 
> 
doug@doug-desktop:~$ ls -l /media/KINGSTON
total 47924
-rwx------ 1 doug root  7342281 2008-07-13 03:32 DVD-RB_v1.282ProNM.exe
-r-x------ 1 doug root       53 2008-08-14 00:54 installing.txt
-r-x------ 1 doug root      289 2008-03-20 10:30 New Text Document (3).txt
-r-x------ 1 doug root 41717538 2008-07-01 08:25 Track 1.wav
drwx------ 2 doug root     4096 2008-08-13 19:55 untitled folder
doug@doug-desktop:~$ chmod u+rw -R /media/KINGSTON
doug@doug-desktop:~$ ls -l /media/KINGSTON
total 47924
-rwx------ 1 doug root  7342281 2008-07-13 03:32 DVD-RB_v1.282ProNM.exe
-rwx------ 1 doug root       53 2008-08-14 00:54 installing.txt
-rwx------ 1 doug root      289 2008-03-20 10:30 New Text Document (3).txt
-rwx------ 1 doug root 41717538 2008-07-01 08:25 Track 1.wav
drwx------ 2 doug root     4096 2008-08-13 19:55 untitled folder
doug@doug-desktop:~$ 





---

### Post by aysiu on 2008-08-15
It's not really a moot point. FAT32 and FAT16 are supposed to mount read/write as well, so there *shouldn't* be any reason to *chmod* or *chown* anything.

The whole *chmod* or *chown* discussion comes up only when something has gone wrong in the mounting process.

It seems the major difference between our results is in how the *chmod* command is invoked. You're using the *u+rw* syntax, and I'm using the *775* syntax. Could that be it?

Either way, *chown* definitely does not work.

The best solution is to just remount the drive with the proper parameters.

---

### Post by mc4man on 2008-08-15
> FAT32 and FAT16 are supposed to mount read/write as well

All my partitions always mount rw, (manual, no fstab) I was thinking more in the context of that some people seem to have windows add files as read only. In the case where there are a number of them it would be easier and faster to use chmod than r.clicking, properties, ect. to change permissions of the affected files.

---

### Post by chrisccoulson on 2008-08-15
> **aysiu said:**
> It's not really a moot point. FAT32 and FAT16 are supposed to mount read/write as well, so there *shouldn't* be any reason to *chmod* or *chown* anything.

The whole *chmod* or *chown* discussion comes up only when something has gone wrong in the mounting process.

It seems the major difference between our results is in how the *chmod* command is invoked. You're using the *u+rw* syntax, and I'm using the *775* syntax. Could that be it?

Either way, *chown* definitely does not work.

The best solution is to just remount the drive with the proper parameters.

Please see my post a few posts earlier. I agree that chown doesn't work at all. The file ownership is defined at mount time. However, while chmod doesn't work in any of the examples you gave, you can still use chmod to change the read-only attribute on a *read-write* FAT32 volume by toggling the write flag, but you need to use the '+w' and '-w' options as opposed to specifying octal permissions.

---

### Post by mc4man on 2008-08-15
Somewhat off topic
If any one knows - is the w flag added to the volume itself or to the volume 'inside' the Os that executed it?
 
It would seem it's to the volume, though I don't know myself.

---

### Post by chrisccoulson on 2008-08-15
> **mc4man said:**
> Somewhat off topic
If any one knows - is the w flag added to the volume itself or to the volume 'inside' the Os that executed it?
 
It would seem it's to the volume, though I don't know myself.

It's stored in the volume. FAT32 supports read-only attributes on individual files, and that is what changing the 'w' flag modifies.

---

### Post by mc4man on 2008-08-15
> It's stored in the volume. FAT32..............
Thanks

So then when you **chown** an ext3/2 volume, ownership is also stored on the volume itself?
as 'seen' here
[http://ubuntuforums.org/showthread.php?t=879434](http://ubuntuforums.org/showthread.php?t=879434)

---

### Post by adept_king on 2008-08-19
i dont know what i am reading, a battle on protocol, politics, or people trying to settle on a paradigm.  

im psyched at the geek potential of linux.  

Q:

how does one decide the permissions of a drive before it gets mounted?

:popcorn:

---

### Post by bodhi.zazen on 2008-08-20
> **adept_king said:**
> i dont know what i am reading, a battle on protocol, politics, or people trying to settle on a paradigm.  

im psyched at the geek potential of linux.  

Q:

how does one decide the permissions of a drive before it gets mounted?

:popcorn:


Setting ownership and permissions depend on the file system. FAT and NTFS it is set at the time of mounting. Linux native file systems it is set with chown and chmod.

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by adept_king on 2008-08-29
what if i am mounting a dvd, drag and drop a file to my desktop, and now its locked?  

this is new to me.  try it please somebody, drag a pdf or an mp3 onto your desktop from a dvd.  is it just me?

at least im allowed to copy or delete these files!

---

### Post by Ptero-4 on 2008-09-24
> **adept_king said:**
> what if i am mounting a dvd, drag and drop a file to my desktop, and now its locked?  

this is new to me.  try it please somebody, drag a pdf or an mp3 onto your desktop from a dvd.  is it just me?

at least im allowed to copy or delete these files!

When you drag something to your desktop. You can change it's permissions the normal way (chown/chmod in cli, properties dialog in nautilus).

---

