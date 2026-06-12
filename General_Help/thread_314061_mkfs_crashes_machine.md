---
title: "mkfs crashes machine"
date: 2006-12-07
forum: General Help
---

### Post by Bubba Ho-Tep on 2006-12-07
I'm having a weird/very frustrating error - 

I'm trying to use a external USB hard disk on a fresh Edgy install.

There is nothing wrong with the disk I know cos I formatted and used it in Windows OK.

I'm trying to put a filesystem on it and mkfs crashes my machine. When I say crash I mean a complete freeze - I can't drop to a terminal, mouse don't work, nothing.

Here's what I'm doing: 

fdisk to create a partition - I use the whole disk it creates 
/dev/sdb1

Then $ sudo mkfs -t ext3 /dev/sdb1

It says it is creating inodes gets a little way thru and then it freezes.

Dunno if it's relevant but initially I was having problems creating the partition - I used fdisk to create a partition which seemed to work and later checked it with "$fdisk -l" which reported that sdb1 "didn't have a valid partition table"

So I whacked it into a windows box created a partition (NTFS) and then reformatted in Linux with fdisk making it ext3. That time fdisk -l reported no problems.

Also  - I was wanting to use xfs on the external USB rather than ext3 but mkfs was complaining it couldn't find mkfs.xfs. A search of apt didn't find it either  - what gives? Where did xfs go under Edgy?

---

### Post by DarthSwampy on 2007-02-07
bump!

---

### Post by halfdan.k on 2007-06-19
I have a nearly identical problem. In my case on an IBM T40 laptop, new Feisty install, while trying to get truecrypt working. 

Following one of several tuts online, I create a truecrypt volume of 10G in my 35G home partition, map it to /dev/mapper/truecrypt* and then
$ sudo mkfs.ext3 /dev/mapper/truecrypt*

which gets to creating inodes and then stalls. Can't drop into terminal, move the mouse, nothing, and no activity registers in my lovely little leds. Left it like that for 7+ hours. Had to "pull the plug" and reboot.  :(
Reproduced same error four times, *but* each time it stalled at one or two inodes higher than previously. I find this quite bizarre and am contemplating whether it is a size related issue, as suggested by the whole WUBI installer 33% stacked thread.
PS: I'm assuming here, that there is no problem with the harddrive, since the install is two days old, and the entire drive was repartitioned and reformatted at that time. 

Any thoughts would be more than welcome.

---

### Post by halfdan.k on 2007-06-19
Update:

Went back, took my own advise and: Reduced size of volume being formatted to 4GB, seemingly the magic number from the Wubi thread 

[http://ubuntuforums.org/showthread.php?t=441577&highlight=33%25+stacked](http://ubuntuforums.org/showthread.php?t=441577&highlight=33%25+stacked)

did the same song and dance, mkfs.ext3 on /dev/mapper/truecrypt0, now gets easily beyond inodes stage, but stalls at the very last step (after creating journals, writing info something or other - sorry didn't remember the exact thing). 

Maybe this post actually belongs in hardware? Anyway - anyone bright enough to tell what the deal is - pls say so. This is getting rather frustrating.

cheers

---

### Post by heineken123 on 2007-06-21
i have exactly the same problem, truecrypt volume 60gb in size, everything stalls at:

mkfs.ext3 /dev/mapper/truecrypt0
mke2fs 1.40-WIP (14-Nov-2006)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
7864320 inodes, 15728639 blocks
786431 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
480 block groups
32768 blocks per group, 32768 fragments per group
16384 inodes per group
Superblock backups stored on blocks:
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
        4096000, 7962624, 11239424

Writing inode tables: 194/480

---

### Post by halfdan.k on 2007-06-22
Interesting - so your volume is quite a lot larger than my initial one was...so the absolute size doesn't appear to be at issue. But I fail to see why/how this could be a truecrypt issue - mkfs.ext3 is a system routine and isn't /dev/mapper/ also system related?

cheers


btw posted a similar thread here, thinking I may have been in the wrong forum (but it would appear to not be a HW issue).

[http://ubuntuforums.org/showthread.php?t=478424](http://ubuntuforums.org/showthread.php?t=478424)

---

### Post by xorwen on 2007-11-17
I have the same problem. The system stucks just a few seconds after execution
```
sudo mkfs.ext3 /dev/mapper/truecrypt0
```
During this time the amount of allocated memory was highly incerasing (hundereds of MB), but the HDD was still working (for 6 hours without any result)

I have Gutsy Gibbon, external USB HDD and truecrypt-4.3a. With command
```
sudo mkfs.vfat /dev/mapper/truecrypt0
```
everything goes fine.

---

### Post by skralljt on 2008-02-22
I have gone through the same song and dance all of you have described, with a 297 gb volume on an sata device.  I get to writing inode tables 195/4xx.  I thought my problem was due to dmraid or something.  I also tried creating the volume with fat initially and then reformatting the truecrypt volume with ext3 but that didn't work, got an error that the filesystem was 0 bytes or something.  My command was sudo mkfs.ext3 /dev/sda1.  I also tried mkfs.ext2.  I get a hard lockup, can't even drop into tty2.  This is frustrating not being able to use my 300 gigabyte volume.  I waited months for truecrypt devs to release a working version for amd64!  I guess I will have to go back to using truecrypt in windows with ntfs, as much as I don't want to.

---

### Post by homunq on 2008-02-26
I am getting the same problem, but over on this thread:

[http://hype-free.blogspot.com/2007/04/installing-and-using-truecrypt-on.html#c3823816039904561860](http://hype-free.blogspot.com/2007/04/installing-and-using-truecrypt-on.html#c3823816039904561860)

people seem to be doing it just fine. I'll post here if I can get it working.

---

