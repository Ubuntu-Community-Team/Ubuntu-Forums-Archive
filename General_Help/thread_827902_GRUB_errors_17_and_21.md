---
title: "GRUB errors 17 and 21"
date: 2008-06-13
forum: General Help
---

### Post by TheAJKMan on 2008-06-13
Okay, I'm quite peeved at the moment. I was busy surfing about 45 odd minutes ago and saw my system slowing to a crawl. Jukebox started greying out and other programs were becoming less and less responsive. I thought I'd just do a quick reboot and carry on. Well, was I ever wrong and in for a nasty shock. I couldn't get back into either of my Ubuntu installations. I tried my 2 hdd individually, both together swopping the jumpers to make them slave/master in turn. All to no avail. I kept getting GRUB errors. The two errors I've kept getting are error 17 and error 21. It just says something along the lines of Starting GRUB, unalbe to load/start(Can't remember now, sorry :( ) ANd then either error 21 or Error 17.

Okay, a bit of background tech type info that might help. I have two hdd, a 40gig and an 80gig. Initially I installed 7.10 on the 40 gig, later adding the 80gig slaved to it. I upgraded to 8.04 on the slaved hdd, that being the 80gig hdd. All was going relatively smoothly till this hiccup. I tried booting up with each hdd individually, with each set to be the master. I tried setting each up as the master with slave and the other hdd then as slave, but no setup worked.

I'm really keen to stay on Linux, but this experience has soured things somewhat for me. Would it help having some kinds of recovery cd/dvd made? If so, how do I make it?

Hope somebody can help.
Thanks
TheAJKMan

---

### Post by drs305 on 2008-06-13
> **TheAJKMan said:**
> 
I'm really keen to stay on Linux, but this experience has soured things somewhat for me. Would it help having some kinds of recovery cd/dvd made? If so, how do I make it?

Hope somebody can help.
Thanks
TheAJKMan

Having a copy of the LiveCD comes in very handy, especially when you have to perform actions that require the system partition to be unmounted. You can download it at 
[Get Ubuntu]("http://www.ubuntu.com/GetUbuntu/download")

And here is a link for restoring grub:
[ How to install Grub from a live Ubuntu cd]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by TheAJKMan on 2008-06-13
Okay, thanks for the reply. Interesting it was, but hasn't helped me solve the problem at all.

okay, here is the sequence of what I did with the 80gig hdd
1) took out the jumper to make the hdd a master only
2)attached ribbon and power to the hdd
3)booted up without the LiveCD -- got GRUB error 17 again.
4)Rebooted machine and hit the Del key to get into the BIOS, saw that it was picking up the hdd in the bios
5)Put LiveCD in and booted up
6)Started Ubuntu up in Safe Graphics mode.
7)Got past the "sudo grub" bit okay
8)type in "find /boot/grub/stage1 and got the following error message --"Error 15: File not found"

Tried the other suggestions listed in that link, but was told stuff along the lines of unrecognised command or directory doesn't exist.

Bottom line is that whilst most of what is on that hdd is expendable, I don't want to scrub it unless there is absolutely no other recourse. There are emails and spreadsheets on there that I would like to have as it is for personal project I'm busy with as part of the greater project. That being the move over to linux and open source entirely. 

PLEASE someone tell me you can help me perform a miracle.

I'm going to reconnect my 40gig hdd and slave the 80gig to it so that I at least can get online for now. Just thought you guys should be told that as it may have some effect on the advice given, it is however no problem to whip cables out and make it a master hdd on it's own too :) *sigh*

---

### Post by drs305 on 2008-06-13
When all this started, if I read it correctly, you were/are able to boot with the grub menu into gutsy 7.10 on the 40 gig and cannot see a menu.lst item to boot into hardy on the 80 gig drive. Is this correct?

If you are now booted into 7.10, would you please post the results of:
```

sudo fdisk -l
cat /etc/fstab
cat /boot/grub/menu.lst

```

If you use uuids, also:
```
sudo blkid
```

That should be enough ;-)

And on which drive is the data you don't want to lose? Not to worry, none of your data has been lost, we just have to get that partition properly mounted again so we can either boot to it or retrieve it.

---

### Post by TheAJKMan on 2008-06-13
err, seems I didn't explain that bit too well. I initially had gutsy insalled on the 40gig and had upgraded to 8.04. That was put on the 80gig drive which was slaved to it. In trying to get onto either of the drives I got GRUB errors on both the drives and so ended up reinstalling 8.04 from scratch on the 40 gig hdd, which is what I am now using. The 80gig hdd is at the moment slaved to the 40gig. As I said, there are spreadsheets, emails that I don't want to loose if it can be helped. There are also wallpapers/avatars and mp3's that I'd also like to get, but those I'm not so concerned about.

---

### Post by drs305 on 2008-06-13
Ok. So you have a fully functioning version of hardy on the 40GB and want to retrieve data from the 80GB? Or was the data on the 40GB? We need to get some information on the partitions and setup. A lot depends on whether or not you partitioned during the installation.

Please post the results of the commands previously mentioned except for the menu.lst  It doesn't appear you will be trying to boot to the old hd.

When you mention 'slaved', are you talking RAID?

---

### Post by TheAJKMan on 2008-06-13
Will run those commands now and post them in the next few minutes. THanks for you time, patience and help. THis newb appreciates it :)

---

### Post by TheAJKMan on 2008-06-13
theajkman@theajkman-desktop:~$ sudo fdisk -l
[sudo] password for theajkman: 

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x76197a10

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4660    37431418+  83  Linux
/dev/sda2            4661        4865     1646662+   5  Extended
/dev/sda5            4661        4865     1646631   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x80004020

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9352    75119908+  83  Linux
/dev/sdb2            9353        9729     3028252+   5  Extended
/dev/sdb5            9353        9729     3028221   82  Linux swap / Solaris
theajkman@theajkman-desktop:~$

---

### Post by TheAJKMan on 2008-06-13
theajkman@theajkman-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=a0032a34-1b53-4f31-8a1d-6512c4aefcb2 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=46581436-af07-405b-9003-5571dd0d76e8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by TheAJKMan on 2008-06-13
theajkman@theajkman-desktop:~$ sudo blkid
/dev/sda1: UUID="a0032a34-1b53-4f31-8a1d-6512c4aefcb2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="46581436-af07-405b-9003-5571dd0d76e8" 
/dev/sdb5: TYPE="swap" UUID="ed0c4100-a41a-4fbe-a88f-994c991baff1"


There it all is, I ran the menu.lst one as well and looking at it if I understand it at all, it looks as though the 80gig hdd isn't listed in it at all :(

---

### Post by drs305 on 2008-06-13
Looking at what you have posted, your 40GB has the standard linux partitions in sda1 (root) and sda5 (swap). Unfortunately, it doesn't show any other existing partitions on which old data might have resided. However, it does jump from the extended partition sda2 to sda5, so there are a couple of partitions that are missing and might be recoverable. I don't know enough about that to offer an opinion.

You can add the following to your fstab to mount the 80GB ext3. I don't know if you will find anything on it.
First, make a mount point and change ownership to yourself. You can name it anything you want, I'll just call it **data**:
```
sudo mkdir /media data
sudo chown -R **username:username** /media/data

```

Make a copy of fstab and open for editing:
```
sudo cp /etc/fstab /etc/fstab.bak1
gksudo gedit /etc/fstab
```

Add the following line to mount the 80GB to /media/data:
```

# /dev/sdb1
/dev/sdb1 /media/data ext3 defaults,user 0 2

```

Then remount and you can see what, if anything, is still on your 80GB:
```
sudo umount -a
sudo mount -a
```

Finally, if you know the name of any of the files you might have lost, you can run a universal search of your partitions to see if they are there:
```
sudo find / -type f -iname **filename_or_partial_filename**
sudo find /media/data -type f -iname **filename_or_partial_filename**

```

I can't offer much other advice except I would not do a lot of writing to either drive until you determine the data is unrecoverable. I suggest you do a new thread with a title including 'data recovery' or something like that and briefly restate the problem. Best of luck.

---

### Post by TheAJKMan on 2008-06-13
Okay, minor problem, when I type in the umount command, I get this message:

umount: /dev/shm: device is busy
umount: /dev: device is busy
umount: /var/run: device is busy
umount: /: device is busy

Which I'm presuming means I cannot unmount and remount. *sigh*  WHy couln't this just be straight forward and simple.

---

### Post by meierfra. on 2008-06-13
> umount: /dev/shm: device is busy
umount: /dev: device is busy
umount: /var/run: device is busy
umount: /: device is busy

Just ignore those messages. They are normal.

---

### Post by drs305 on 2008-06-13
> **TheAJKMan said:**
> Okay, minor problem, when I type in the umount command, I get this message:

umount: /dev/shm: device is busy
umount: /dev: device is busy
umount: /var/run: device is busy
umount: /: device is busy

Which I'm presuming means I cannot unmount and remount. *sigh*  WHy couln't this just be straight forward and simple.

Normal, as was said. The command can't unmount certain items in use. I should have warned you. ;-)

---

### Post by Deadheded on 2008-06-13
I have had some of the same problems in the past.  I use to run 3 IDE HDs and one SCSI drive.  If I took out any one of the IDE drives (Ubuntu was on the SCSI) I would get the grup 21 error and not be able to boot to any drive.  I don't have the exact commands I used to fix it but I may be able to help a little and have others fill in the gaps. 

First I had to change the grub file menu.lst to reflect the proper hd0,0 numbers.

Then I had to set the drive ID's.  I am sorry but I don't remember exactly how I did this but the info is on the forums somewhere.  I believe I used some grub commands.  I hope someone here can help fill in the gaps for you.

---

### Post by TheAJKMan on 2008-06-13
I'll try the find commands anyways and see if it picks up anything. WOuld be a great pity to loose all that data. Thanks for your time, help and patience anyways. It is greatly appreciated.

---

