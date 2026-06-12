---
title: "Fix dead hard drive?"
date: 2013-01-21
forum: General Help
---

### Post by TheGuyWithTheFace on 2013-01-21
Hi everyone!

A while back, I upgraded my laptop to an SSD. (Best thing I've ever done!) At the time, I was dual booting windows and Ubuntu on a 600Gb HDD. When I went to a 256GB SSD, I concluded that windows was a waste of space, and did not put it on the SSD. (Second best thing I've ever done! :D) I kept the old hard drive though, and now, unfortunately, I have to use windows 7 for a class I'm taking. I know this is not a windows forum, but if I could boot the HDD, I have a plan to move windows to virtualbox, so that's taken care of. The issue is, when I plug it into my laptop, it won't boot.

Once before, I had to use it, and when I tried to plug it in via SATA to USB connection, I got grub, and my old Ubuntu install worked, but I had to plug it into the original spot inside my laptop to get windows to boot without a BSOD. Now, though, when I plugged it in, (via a USB connection first, then when that didn't work, I plugged it in directly through the SATA 2 port.) Grub failed to work at all. I had a spare USB lying around, so I tried to do a grub-repair, which has worked for me in the past: 

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Alas, when I finished that and tried to start up, I got a disk read error before I even got to GRUB...

When I try to mount the hard drive from a running Ubuntu 12.04 or Lubuntu 12.10 install, I get this error:

> 
Error mounting: mount exited with exit code 13: ntfs_mst_post_read_fixup_warn: magic: 0x43425355  size: 4096   usa_ofs: 2002  usa_count: 65535: Invalid argument
Actual VCN (0x80000a0b9310000) of index buffer is different from expected VCN (0x0).
Failed to mount '/dev/sdb2': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.


Gparted reports that the partitions are there, but the file type for the ubuntu partition is not recognized, and the windows partition is complaining about bad sectors or something, but those errors were there when I was constantly using the old hard drive before I upgraded.

My question is, did I just completely fry my old hard drive, or is there a way I could revive it?

Also, I put this in general help, because I'm not sure if my hardware issue is caused by a software malfunction, (i.e. grub), but to any moderators reading this, should this be in the hardware section?

---

### Post by sudodus on 2013-01-21
[COLOR="RoyalBlue"][/COLOR]No I don't think you fried your HDD. Maybe you have damaged the linux file system (root or /).

Boot from another drive and do not mount any partition on this HDD. Unmount if they are auto-mounted, and check with
```
df
```

Then you can try to repair the file system with
```
sudo e2fsck -f /dev/sd[COLOR="red"]x[/COLOR][COLOR="blue"]**y**[/COLOR]
```
where [COLOR="Red"]x[/COLOR] is the drive letter, typically [COLOR="red"]a[/COLOR] if only one internal drive, and [COLOR="blue"]**y**[/COLOR] is the partition number.

---

### Post by TheGuyWithTheFace on 2013-01-21
Hi sudodus, thanks for your quick response!

I'm not sure what I'm looking for with the df command, but here's the output:

> 
/dev/sda1             19684632  7395764  11288932  40% /
udev                   2997220        4   2997216   1% /dev
tmpfs                  3009232       12   3009220   1% /tmp
tmpfs                  1203696      956   1202740   1% /run
none                      5120        8      5112   1% /run/lock
none                   3009232      636   3008596   1% /run/shm
tmpfs                  3009232        0   3009232   0% /var/spool
tmpfs                  3009232       92   3009140   1% /var/tmp
tmpfs                  3009232      844   3008388   1% /var/log
/dev/sda2            225955260 70147276 144330076  33% /home
/home/TheGuy/.Private 225955260 70147276 144330076  33% /home/TheGuy


The e2fsck command didn't seem very happy with me:

> 
e2fsck 1.42 (29-Nov-2011)
e2fsck: Superblock invalid, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/sdb

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>


I'm not sure what the super-block is, or the magic number, but I know I don't have any ext2 filesystems on there...

---

### Post by sudodus on 2013-01-21
> **TheGuyWithTheFace said:**
> 
The e2fsck command didn't seem very happy with me:

I'm sorry, you should run e2fsck on partitions so in your case

```
sudo e2fsck -f /dev/sda1
sudo e2fsck -f /dev/sda2
```

> 

I'm not sure what the super-block is, or the magic number, but I know I don't have any ext2 filesystems on there...

---

### Post by TheGuyWithTheFace on 2013-01-21
I just read (some of) this article:
[http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html](http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html)

And it seems pretty helpful.

I used mke2fs -n /dev/sdb to see the info about the hdd, and got this:

> 
mke2fs 1.42 (29-Nov-2011)
/dev/sdb is entire device, not just one partition!
Proceed anyway? (y,n) y
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
39075840 inodes, 156282965 blocks
7814148 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4294967296
4770 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
	4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
	102400000


I just picked one of the superblock backups, and used the suggested command:

e2fsck -f -b 819200 /dev/sdb

and got the same error as in my previous post. *sigh* I'll keep trying...

---

### Post by TheGuyWithTheFace on 2013-01-21
Sorry, I didn't realize in my last post that you had already replied.

Ok, so I tried: 

sudo e2fsck -f /dev/sdb2
(sdb2 was my windows partition, which is what I really wanted,but one step at a time...)

Not surprisingly, I got the same error as before.

I then tried:

sudo e2fsck -f /dev/sdb5

Which is my Ubuntu partition, and I got this:

> 
e2fsck 1.42 (29-Nov-2011)
e2fsck: Superblock invalid, trying backup blocks...
Superblock has an invalid journal (inode 8).
Clear<y>? 


I'm a little afraid to "clear" it, so I'm just leaving that terminal window open for now...

---

### Post by alphaamanitin on 2013-01-21
If I understand correctly you want to boot into the windows install on the now, external HDD?  AFAIK, Windows WILL NOT boot from external drives without a bit of work during the install.  I am not sure you can get it to boot once removing the drive from the computer.

AlphaA

---

### Post by TheGuyWithTheFace on 2013-01-21
Yes, a while back, to get it to boot I had to put it back in. The issue is now even when it's inside my computer I can't boot into it. (right now It's connected via USB so I can try to restore it, though.) Once I get Ubuntu/GRUB back, my plan is to put it back into my computer, boot into windoze, factory reset it, take an image of the hard drive in .iso format, and then use that .iso to make a virtualbox install on my regular ssd. That may be a little too much information, but for now my chief concern is booting into it at all...

---

### Post by alphaamanitin on 2013-01-21
You can try putting the drive back in, and running the windows boot manager repair program from a windows install disk, or use SuperGrub to check.  It makes me think that the MBR on the drive for windows is damaged.  

AlphaA

---

### Post by sudodus on 2013-01-21
This is your second drive /dev/sdb

> **TheGuyWithTheFace said:**
> 
sudo e2fsck -f /dev/sdb2
(sdb2 was my windows partition, which is what I really wanted,but one step at a time...)

Not surprisingly, I got the same error as before.

I then tried:

sudo e2fsck -f /dev/sdb5

Which is my Ubuntu partition, and I got this:

I'm a little afraid to "clear" it, so I'm just leaving that terminal window open for now...

I think you can clear the invalid journal (inode 8). Let us hope that will solve your problem. Maybe there will be another error to be fixed too.

From your earler post (post #3) you had mounted only your first drive /dev/sda
> ```

/dev/sda1 19684632 7395764 11288932 40% /
/dev/sda2 225955260 70147276 144330076 33% /home
```
Is this correct? According to this listing of [FONT="Courier New"][SIZE="3"]df[/SIZE][/FONT], your root partition is
/dev/sda1 and your home partition is /dev/sda2

Anyway you should use Windows tools to repair windows partitions
```
chkdsk /f X:
```
Only use e2fsck for linux ext partitions!

---

### Post by sudodus on 2013-01-21
It is possible to use preinstallation environment tools to repair windows, simple repair like chkdsk /f

1. a Windows install disk
2. BartPE
3. Windows PE
4. Windows 7 PE

And as mentioned by alphaamanitin, there are special boot disks with repair tools for Windows.

---

### Post by TheGuyWithTheFace on 2013-01-21
> **alphaamanitin said:**
> You can try putting the drive back in, and running the windows boot manager repair program from a windows install disk, or use SuperGrub to check.  It makes me think that the MBR on the drive for windows is damaged.  

AlphaA

Yes, I forgot to mention I tried a windows repair disk, but for some reason that gave me the same disk read error. :confused:

> **sudodus said:**
> It is possible to use preinstallation environment tools to repair windows, simple repair like chkdsk /f

1. a Windows install disk
2. BartPE
3. Windows PE
4. Windows 7 PE


Alright, I'm looking into BartPE, thanks for that. The e2fsck -f /dev/sdb5 command is still running, at this point I'm just spamming the y key, I'll update when I'm done with that.

---

### Post by TheGuyWithTheFace on 2013-01-21
Well, the e2fsck -f /dev/sdb5 command is taking forever to move along, so I figured I'd give an update. Here's the last thing it outputed:

> 
clone_file_block: internal error: can't find dup_blk for 18907964


Just for the heck of it, I decided to fire up gparted to see what it said about my HDD. It still has the error on my windows partition, but I'm pleased to say it recognized my Ubuntu partition was ext4! Granted, it was still complaining that my superblock magic number was invalid, and that it couldn't read the contents, but that's progress! Not bad considering the repair command thingy still hasn't finished.

---

### Post by TheGuyWithTheFace on 2013-01-21
e2fsck -f /dev/sdb5 is still running, and it's still stuck on that same error. :( If I were to kill that process, do you think it will mess things up further, or will I keep what progress I've made, or what?

---

### Post by sudodus on 2013-01-21
> **TheGuyWithTheFace said:**
> e2fsck -f /dev/sdb5 is still running, and it's still stuck on that same error. :( If I were to kill that process, do you think it will mess things up further, or will I keep what progress I've made, or what?
Give it a chance to finish! It can take hours, depending on what it needs to do and the speed and size of the drive. I think you connected via USB2, so it will be slow, much slower than an internal SATA connection.

Good luck :-)

---

### Post by TheGuyWithTheFace on 2013-02-05
Well, call me impatient, but I eventually did give up... That being said, I really appreciate everyone's quick responses, and since I believe they will be very useful to anyone else with my problem, I'm still gonna mark this as solved.

---

### Post by calebunleashed on 2013-05-10
Howdy,

I'm getting this exact same error. @TheGuyWithTheFace how long did you wait until you gave up? And how big was your HDD? 20/40/100/500GB?

I using a live CD and I received the following error when I tried to mount the LVM:

[FONT=courier new]mount wrong fs type bad option bad superblock on /dev/mapper/
[/FONT]
And I received the following error when I first tried to run e2fsck:
[FONT=courier new]e2fsck -y -f /dev/[/FONT][FONT=courier new]mapper[/FONT][FONT=courier new]/vgname/lvname[/FONT]
[FONT=courier new]The filesystem size (according to the superblock) is 12453462 blocks[/FONT]
[FONT=courier new]The physical size of the device is 10093482 blocks[/FONT]
[FONT=courier new]Either the superblock or the partition table is likely to be corrupt![/FONT]

So I ran the following command:
[FONT=courier new]mke2fs -S /dev/mapper/vgname/lvname[/FONT]

It didn't take very long, and after that I ran this command:
[FONT=courier new]e2fsck -y -f /dev/[/FONT][FONT=courier new]mapper[/FONT][FONT=courier new]/vgname/lvname[/FONT]

And this is pumping out the following error:
[FONT=courier new]clone_file_block: internal error: can't find dup_blk for <inode_number>[/FONT]

I loosely followed these instructions: [http://ubuntuforums.org/showthread.php?t=1681972&page=5&p=10434656#post10434656](http://ubuntuforums.org/showthread.php?t=1681972&page=5&p=10434656#post10434656)

Any help would be appreciated. I lost about 2 weeks worth of work.

---

### Post by TheGuyWithTheFace on 2013-05-10
Hello calebunleashed, welcome to the forums!

The drive size was 600Gb, and I waited for at least a day or so. (I think, but the details are a bit fuzzy now.) Granted, that was a cheap laptop hard drive, so yours may be quite a bit faster. Aside from that I'm afraid I don't have much to contribute, I actually don't know a whole lot about how the filesystem works on that level.
 
I'm sorry I don't have more to offer, but tell me if there's anything I can do to help, and good luck!

---

### Post by sudodus on 2013-05-11
Hello calebunleashed,

*Start*

You can start by checking the ***S.M.A.R.T.*** status, either from the BIOS menus or with the program ***smartctl*** (install smartmontools).

```
 sudo apt-get install smartmontools
```

* Backup*

If your data are valuable enough (and two weeks of work should be), suggest that you clone the faulty disk to another drive (an external HDD drive) using ***ddrescue*** if there are hardware errors, or otherwise some other cloning tool would do fine, for example ***Clonezilla***.

There is a vert good tutorial in the manual file of ddrescue

```
info ddrescue
```

*Repair*

Then, you can start trying to restore the file system with different methods. These methods are powerful, but there is a risk, that they cause more damage than improvement. For example try ***testdisk ***or*** gpart***. You find information about them and how to get them on the Internet. The best thing is cases like this is to boot the computer from another drive (not the drive with the bad partition). 

*Recovery*

If there is no way to restore the file system, you can try ***PhotoRec***, which can recover data directly from the storage area on the disk without help from the file system. Originally recovering photos from flash cards, it is now recovering most common file types for documents etc. The file names and the directory structure are not recovered, so you have to do a lot of manual work to restore the most important files.

---

