---
title: "strange message while using partimage!!"
date: 2007-07-27
forum: General Help
---

### Post by yehudaco on 2007-07-27
hi, i get a strange announcment when i try to backup my file system using partimage.
the back up start, and after a while i get a message "cannot create  temp file sdb3 no space left on device" the whole file system partition is 22 gb but only 6 used, and the backup is made to a different partition which has 198 gb free!!! and still! i get this message!
any idea why???

---

### Post by yehudaco on 2007-07-27
anybody??!!

---

### Post by dcstar on 2007-07-28
> **yehudaco said:**
> hi, i get a strange announcment when i try to backup my file system using partimage.
the back up start, and after a while i get a message "cannot create  temp file sdb3 no space left on device" the whole file system partition is 22 gb but only 6 used, and the backup is made to a different partition which has 198 gb free!!! and still! i get this message!
any idea why???

It may be using the sdb3 file system as part of the compression phase of the backup - if the backup size is greater than what is available in your /tmp folder then this error may well occur.

Turn off compression and see if it still occurs.

---

### Post by little_penguin on 2007-07-28
>  Originally Posted by yehudaco  View Post
hi, i get a strange announcment when i try to backup my file system using partimage.
the back up start, and after a while i get a message "cannot create temp file sdb3 no space left on device" the whole file system partition is 22 gb but only 6 used, and the backup is made to a different partition which has 198 gb free!!! and still! i get this message!
any idea why???

Hi yehudaco,

You have to make sure the partition you want to save the image to is mounted first, and that you enter the full path to the mount point in the save image as field. I had the same error message once and that turned out to be the reason.

Mount your sdb3 partition to, say, /media/sdb3, depending on your system:

sudo mount /dev/sdb3 /media/sdb3

Then in partimage:

save image file as
/media/sdb3/yourimagefilename

Hope it helps :-)
little_penguin

---

### Post by yehudaco on 2007-07-28
when i try to mount media/sdb3 i get this:
yehuda@Yehuda:~$ sudo mount /dev/sdb3 /media/sdb3
Password:
mount: /dev/sdb3 already mounted or /media/sdb3 busy
mount: according to mtab, /dev/disk/by-uuid/7E56142017196814 is already mounted on /media/sdb3
yehuda@Yehuda:~$ 

when i try to save the backup to the same place ( /media/sdb3/System.Backup.001 ) i get a message that tells me that the file ##@#@#@.tmp can't be written to   /media/sdb3/ and i have to check access rights and if i have enough free space....

and if i try to backup to  /sdb3/System.Backup.001 it would work fine allright but ufter backing up around 20% which is 500mib approx it would say he doesn't have enough space!!! while it has 198gb free! and the whole partition i try to backup is 21gb in total including the free space which he doesn't supose to backup!!
any idea what the problem might be??

---

### Post by little_penguin on 2007-07-28
> **yehudaco said:**
> when i try to mount media/sdb3 i get this:
yehuda@Yehuda:~$ sudo mount /dev/sdb3 /media/sdb3
Password:
mount: /dev/sdb3 already mounted or /media/sdb3 busy
mount: according to mtab, /dev/disk/by-uuid/7E56142017196814 is already mounted on /media/sdb3
yehuda@Yehuda:~$ 

when i try to save the backup to the same place ( /media/sdb3/System.Backup.001 ) i get a message that tells me that the file ##@#@#@.tmp can't be written to   /media/sdb3/ and i have to check access rights and if i have enough free space....

and if i try to backup to  /sdb3/System.Backup.001 it would work fine allright but ufter backing up around 20% which is 500mib approx it would say he doesn't have enough space!!! while it has 198gb free! and the whole partition i try to backup is 21gb in total including the free space which he doesn't supose to backup!!
any idea what the problem might be??

Hi yehudaco,

I am taking a bit of a guess here, but it could be that plugged-in USB sticks or drives might have shifted the actual device name/number? Possibly a 512mb stick? Your partition may no longer be sdb3, try

df -h

to check where things are mounted and to see whether the partition you want to save to is in fact sdb3 and if not, what name it has

Hope it helps,
little_penguin

---

### Post by yehudaco on 2007-07-28
little_penguin - thank you very much for your help!! this is the output for what you've said:
yehuda@Yehuda:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1              22G  4.7G   16G  24% /
varrun                505M  280K  505M   1% /var/run
varlock               505M     0  505M   0% /var/lock
procbususb            505M  116K  505M   1% /proc/bus/usb
udev                  505M  116K  505M   1% /dev
devshm                505M     0  505M   0% /dev/shm
lrm                   505M   33M  472M   7% /lib/modules/2.6.20-16-generic/volatile
/dev/disk/by-uuid/94A07D69A07D532A
                       37G   29G  7.7G  79% /media/sda1
/dev/sda2             3.8G  3.4G  400M  90% /media/sda2
/dev/disk/by-uuid/8CE8058DE805772C
                       35G   34G  1.3G  97% /media/sda5
/dev/disk/by-uuid/7E56142017196814
                      210G   23G  188G  11% /media/sdb3
yehuda@Yehuda:~$ 

i'm not really an expert but if i understand it correctly every seem fine - the sdb3 partition is as big as i thought, there really not suppose to be a space prob. is there?

---

### Post by az on 2007-07-28
Partimage copies the whole partition, so it will use 22Gb, not just the space on the filesystem (6GB).  To avoid this, you can create a file in the filesystem and fill it with zeros until you run out of space, then delete the file.

If your error message is verbatim, sdb3 is not the device, but the file name.  If it is trying to same a file called "sbd3" that is 22 Gigs big on a filesystem with 16 Gb free, that would explain it.

There is no partimage option for using a different temp location.  Perhaps you need to free up some space, or mount a temporary temp filesystem over /tmp

---

### Post by SPr on 2007-07-28
AFAIK the tmp file is written to /media/sdb3. Do you have permission to write to that device?

---

### Post by yehudaco on 2007-07-28
so, if i understood correctly i can't save the backup to other partition but to sbd1? and this partition is short of free space?it is sound strange because this way it will always be short of free space...
anyhow, how do i mount a temporary temp filesystem over /tmp?
how do i manage to make this backup???

---

### Post by SPr on 2007-07-28
> **SPr said:**
> AFAIK the tmp file is written to /media/sdb3. Do you have permission to write to that device?

If you save the image to /media/sbd3 then the temp file will also be stored on /media/sbd3 and erased when the image is made. I use partimage on the SystemRecoveryDisk and that version always uses the same device to store the temp file and the image. Do you have the correct permissions to write to /media/sbd3?

---

### Post by yehudaco on 2007-07-28
yes, i think i have the permmission, how can i verify it?
and how do i make tmp directory so it would write on?
 edit: and in case i don't have the permission, how can i get it? by using mount (you can see in the previous posts) it didn't help, partimage would still tell me something about the tmp file.,...

---

### Post by little_penguin on 2007-07-28
In addition to the previous poster's question about whether you have the correct access permissions to your sdb3 partition, I am also wondering what filesystem that partition is? Is it perhaps a Windows NTFS partition, e.g. as used by XP/Vista? That might explain a couple of things. So things to check are:

1) Do you have write access permissions to sdb3?

2) What filesystem is that partition using - is it Windows NTFS, FAT32 or linux native EXT3?

Regards,
little_penguin

---

### Post by SPr on 2007-07-28
ls -l /media/sdb3 will show the permissions, owner and group etc.

I'm sure the temp file wont be written to /tmp but to /media/sdb3/RANDOM.tmp. This file will be deleted after the image is made. You don't need to create this file.

Which filesystem is used is also a very good question.

---

### Post by yehudaco on 2007-07-28
well i think we wrote at the same time or something cause i answered the second part just now but i checked again  i think i have permission to create and delete files that what it says in the 
file browser > properties > permissions
and as for filesystem - indeed ntfs on the sdb3 - the partition i try to make the backup on! the one i try to backup is  - sdb1 filesystem ext3
edit:
yehuda@Yehuda:~$ ls -l /media/sdb3
total 12
drwxrwxrwx 1 root root    0 2007-07-16 14:37 BackupFile
drwxrwxrwx 1 root root    0 2007-07-27 09:50 Docs
drwxrwxrwx 1 root root 4096 2007-07-25 22:43 FireFoxDownloads
drwxrwxrwx 1 root root    0 2007-07-13 13:43 Fun
drwxrwxrwx 1 root root 4096 2007-07-25 13:39 Logs
drwxrwxrwx 1 root root    0 2007-07-23 08:27 RECYCLER
drwxrwxrwx 1 root root 4096 2007-07-15 18:08 System Volume Information
yehuda@Yehuda:~$

---

### Post by little_penguin on 2007-07-28
> **yehudaco said:**
> well i think we wrote at the same time or something cause i answered the second part just now but i checked again  i think i have permission to create and delete files that what it says in the 
file browser > properties > permissions
and as for filesystem - indeed ntfs on the sdb3 - the partition i try to make the backup on! the one i try to backup is  - sdb1 filesystem ext3
edit:
yehuda@Yehuda:~$ ls -l /media/sdb3
total 12
drwxrwxrwx 1 root root    0 2007-07-16 14:37 BackupFile
drwxrwxrwx 1 root root    0 2007-07-27 09:50 Docs
drwxrwxrwx 1 root root 4096 2007-07-25 22:43 FireFoxDownloads
drwxrwxrwx 1 root root    0 2007-07-13 13:43 Fun
drwxrwxrwx 1 root root 4096 2007-07-25 13:39 Logs
drwxrwxrwx 1 root root    0 2007-07-23 08:27 RECYCLER
drwxrwxrwx 1 root root 4096 2007-07-15 18:08 System Volume Information
yehuda@Yehuda:~$

Hi yehudaco,

Ahh, thought it might be...To write to an NTFS partition, you will need ntfs-3g, because linux AFAIK only writes directly to windows FAT32 without needing extra tools. There should be plenty of info on ntfs-3g in the forum, I don't actually use it myself, so I can't give you any detailed help on that. I just know that you need it to write to NTFS partitions.. Someone else will be able to help you, I'm sure.

Regards,
little_penguin

---

### Post by SPr on 2007-07-28
nm

---

### Post by crisb on 2008-01-26
hi,

I ve just gone through the same process, but finally managed to make the image of the partitions.

In my case the problem was this> 
the partition-to-save-table in Partimage gave me /dev/sdb1 as the path to the external harddrive which I wanted to use as the goal for the backup image. So I tried to use that path as the path for the image-file (/dev/sdb1/myimagename) - and got the error message that your initial posting quotes.
BUT when I used the **mount point** of my external harddrive (/media/nameofexternalpartition) in the goal path for the partition image (/media/nameofexternalpartition/myimagename) it WORKED!

(you find the mount point of a volume in ubuntus file-browser > computer > properties of the respective volume > volume)

hope this helps you!

---

