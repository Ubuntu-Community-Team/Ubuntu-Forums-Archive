---
title: "Reconnecting/recovering second hd"
date: 2006-07-28
forum: General Help
---

### Post by stulesnett on 2006-07-28
I have experience a MASTER HD crash and replaced it.  The master disk has been replaced and I've started rebuilding the system.  My slave HD seem fine but I do not seem to able reconnect of access the slave's HD information.  The initial mount hdb and hdb1 /photos which turn into several sub directories.

I did try to modify the fstab to include the device.

Can anyone provide some assistance.

Thanks.

Stu

---

### Post by ifokkema on 2006-07-29
Hi,

Possibly, the former 'hdb' is no longer 'hdb'. What's the output of this command:
```
sudo fdisk -l
```
It should list both hard drives.

---

### Post by stulesnett on 2006-07-29
Thank the information.  When I ran the fdisk -l, it left the disk as hdb1 but says it's a fat16(??) disk enstead of ext3.  I've attempted to change the fstab to 'vfat' format but it still doesn't find it.  I tried changing it to a ext3 and did a mount but received a lock error.:-(

---

### Post by ifokkema on 2006-07-30
OK, now we must be careful not to damage the files on that disk. I assume the data is valuable to you.
- Double check if the /dev/hdb drive is the one you're looking for. When running the fdisk -l command, it tells you the total size of the disk. Does that look familiar? Also, run:
```
cat /proc/ide/hdb/model
```
Verify that this is the HD you want to access.
- Are you sure it was an ext3 partition?

Run gparted:
```
sudo apt-get install gparted
sudo gparted
```
- Select the hdb disk in the top right of the screen.
- Make sure the partition is not mounted (right-click -> unmount).
- Does is say it's a FAT16 partition?

Now you have two options. If you are sure that is was an ext3 partition, you can change it back to ext3 using gparted. Then run a filesystem check (fsck) on that drive. (READ THE NOTE AT THE BOTTOM)
```
sudo fsck.ext3 -f /dev/hdb1
```
Be careful because if this disk was not ext3, the filesystem check will choke and possibly remove all data in the process of trying to repair the disk.

Other option is to run fsck.vfat straight away, without changing the filesystem type to ext3. Here also, the filesystem check may choke if this disk was not FAT16 and possibly remove all data in the process of trying to repair the disk.

NOTE - Before doing a filesystem check, it may be possible to use debugfs to try and verify some of the data on the drive. I haven't got much experience with debugfs myself, but it may provide a clue about what's on that disk and see if it's still healthy - without damaging something.

Also, a fsck will only possibly damage the data on the disk if you actually press 'y' somewhere in the process if it asks you if you want it to fix something.

Good luck!

---

### Post by stulesnett on 2006-08-02
Sorry, I have not had opportunity to try this action out yet, possibly tonight.  Since I've put the new disk drive in, re-installed Apache 2.0, PHP 5.0, MYSQL and phpmyadmin a password problem has arisen and caught my attention.  Basically because until I get these application back up and running the information on the 2 HD isn't required.

Apache 2.0 Virtural hosting appears to working fine, PhP 5.0 is up and the test configuration is working.  Mysql continues to ask for a PASSWORD?? I've remove MYSQL and phpmyadmin and re-installed them but continue to hit this wall.  MYSQL Server is running and I've looked at the tables, created a second DB table and added a user but it continues to reject direct access (slesnett.localhost denied) and requests a password.

Thanks again.

---

### Post by ifokkema on 2006-08-03
> **stulesnett said:**
> Apache 2.0 Virtural hosting appears to working fine, PhP 5.0 is up and the test configuration is working.  Mysql continues to ask for a PASSWORD?? I've remove MYSQL and phpmyadmin and re-installed them but continue to hit this wall.
Did you PURGE the MySQL packages, or just uninstalled? Purging them will remove any config files as well. Use apt-get remove --purge to purge the packages.

> **stulesnett said:**
> MYSQL Server is running and I've looked at the tables, created a second DB table and added a user but it continues to reject direct access (slesnett.localhost denied) and requests a password.
If you can create a table and add a user, you're connected. I'm not sure what you mean by 'direct access (slesnett.localhost denied)'.

---

### Post by stulesnett on 2006-08-03
HD problem continuation, I tried your suggestion on the "cat/proc/ide/hdb/model" and received the correct label "WDC AC2700 H" and yes, the size from "fdisk -l" looks correct.

I could not find gpart on my ubuntu CD, so I have downloaded the application from Debian but ran out of time last night.

MYSQl, I did a remove on both Mysql and phpmyadmin and then a re-install.

Stu

---

### Post by stulesnett on 2006-08-09
I have gotten Apache, php and mysql running.  I have also gotten gparted downloaded, installed and running.  I'm not sure what gparted is subposed to accomplish.  It tells me that I have 2 hd and the seconded one is EXT 3.  I did a mount on /photos but nothing happens and the directories ??

fsck.ext3 -f /dev/hdb1 
e2fsck 1.38
Pass1 checking inodes, blocks and sizes
Error reading black 163852 (short read) while inodes scanIgnor error (y) I type no
terminated e2fsck

Stu

---

### Post by ifokkema on 2006-08-10
> **stulesnett said:**
> I'm not sure what gparted is subposed to accomplish.  It tells me that I have 2 hd and the seconded one is EXT 3.
OK, that's much better than FAT16 :)

> **stulesnett said:**
> I did a mount on /photos but nothing happens and the directories ??
No errors?

> **stulesnett said:**
> 
fsck.ext3 -f /dev/hdb1 
e2fsck 1.38
Pass1 checking inodes, blocks and sizes
Error reading black 163852 (short read) while inodes scanIgnor error (y) I type no
terminated e2fsck

I've looked up this error on Google, figured it was "Error reading block #### (Attempt to read block from filesystem resulted in short read)", and I believe most people loose their HD when it returns errors as these. But hey, as the disk is recognized as ext3 correctly, let's give it a try:

```
sudo fsck.ext3 -cf /dev/hdb1
```
This runs a bad block test, as well as checking the structure of the file system. It can take quite some time to run. But if it returns an error, just select to fix it. It can't get any worse than this anyway :)

---

### Post by stulesnett on 2006-08-14
e2fsck 1.38 (30-Jun-2005)
Checking for bad blocks (read-only test):             704/         178156
            960/         178156
                done                        156
Pass 1: Checking inodes, blocks, and sizes

Running additional passes to resolve blocks claimed by more than one inode...
Pass 1B: Rescanning for multiply-claimed blocks
Multiply-claimed block(s) in inode 8: 960 975 1151 1209 1219 1226 1288 1347 1348  1404 1462 2360 2396 2454 2456 2511
Pass 1C: Scanning directories for inodes with multiply-claimed blocks
Pass 1D: Reconciling multiply-claimed blocks
(There are 0 inodes containing multiply-claimed blocks.)

File <The journal inode> (inode #8, mod time Mon Jun 12 12:28:53 2006)
  has 16 multiply-claimed block(s), shared with 1 file(s):
        <The bad blocks inode> (inode #1, mod time Thu Aug 10 21:43:44 2006)
Clone multiply-claimed blocks<y>? yes

Error reading block 975 (Attempt to read block from filesystem resulted in short  read).  Ignore error<y>? yes

Force rewrite<y>? yes

Error reading block 1151 (Attempt to read block from filesystem resulted in shor t read).  Ignore error<y>? yes

Force rewrite<y>? yes

Error reading block 1209 (Attempt to read block from filesystem resulted in shor t read).  Ignore error<y>? yes

Force rewrite<y>? yes

Error reading block 1219 (Attempt to read block from filesystem resulted in shor t read).  Ignore error<y>? yes

Force rewrite<y>? yes

Error reading block 1226 (Attempt to read block from filesystem resulted in shor t read).  Ignore error<y>? yes

Force rewrite<y>? yes

Error reading block 1347 (Attempt to read block from filesystem resulted in short read).  Ignore error<y>? yes

Force rewrite<y>? yes

Error reading block 1404 (Attempt to read block from filesystem resulted in short read).  Ignore error<y>? yes

Force rewrite<y>? yes

Error reading block 1462 (Attempt to read block from filesystem resulted in short read).  Ignore error<y>? yes

Force rewrite<y>? yes

Error reading block 2396 (Attempt to read block from filesystem resulted in short read).  Ignore error<y>? yes

Force rewrite<y>? yes

Error reading block 2454 (Attempt to read block from filesystem resulted in short read).  Ignore error<y>? yes

Force rewrite<y>? yes

Error reading block 2511 (Attempt to read block from filesystem resulted in short read).  Ignore error<y>? yes

Force rewrite<y>? yes

Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
/lost+found not found.  Create<y>? yes

Pass 4: Checking reference counts
Pass 5: Checking group summary information
Free blocks count wrong for group #5 (1449, counted=1820).
Fix<y>? yes

Free blocks count wrong (158640, counted=159011).
Fix<y>? yes

Inode bitmap differences:  +(74497--74528) +(75617--75680) +(76737--76768) +(77345--89088)
Fix<y>? yes

Free inodes count wrong for group #5 (14848, counted=2976).
Fix<y>? yes

Free inodes count wrong (89074, counted=77202).
Fix<y>? yes


/dev/hdb1: ***** FILE SYSTEM WAS MODIFIED *****
/dev/hdb1: 11886/89088 files (0.0% non-contiguous), 19145/178156 blocks

This ran for over 3 hours but I'm have not recovered the files nor been able for Ubuntu to find them.

Stu

---

### Post by ifokkema on 2006-08-14
Seems like output I've seen before on an disk of mine.
1) For now, don't put stuff there that you can't risk loosing. You might want to try and decrease the maximum amount of mounts before the system checks your drive again. Use tune2fs for that (see the manual page for that command).

2) Your files may be in the lost+found directory. That directory is used to put lost files in, but I can't find any errors in the above list about moving unallocated inodes there. But it's worth a shot. Your journal inode was messed up, but since I don't see any other errors above related to that, I think the superblock was OK...

Well anyway, just check the lost+found directory and see if anything is in there...

---

