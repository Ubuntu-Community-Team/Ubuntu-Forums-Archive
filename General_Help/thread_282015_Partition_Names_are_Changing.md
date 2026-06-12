---
title: "Partition Names are Changing"
date: 2006-10-22
forum: General Help
---

### Post by cssutto on 2006-10-22
I don't know why I have these weird problems, but here goes:

I have a Maxtor 200G External Drive I use for backups.

It has four partitions.

Ubuntu has chosen to name them.

I back up to these partitions with rsync.  I have had the strange problem of backups not being in the correct partition.  I want to keep /home backups, // backups and W2K backups in separate partitions and they get mixed up.

And backups ended in / and I could not figure out why.

I finally noticed that the reason seems to be that Ubuntu changes the names of two partitions and sometimes creates an additional one (in name only).

df will return  /media/LOCAL DISK
and
/media/LOCAL DISK-1 for two of the partitions.

Tomorrow it might be /media/LOCAL DISK
media/LOCAL DISK-1
media/LOCAL DISK-2

Right now, df returns the former.

But if  I cd /media
ls
I get the following:
cdrom   floppy0   hda1  LOCAL DISK    usb      usbdisk-1  usbdisk-4
cdrom0  H:        hda2  LOCAL DISK-1  usb0     usbdisk-2  usbdisk-5
floppy  H_    ~1  hda6  LOCAL DISK-2  usbdisk  usbdisk-3

Remember that the DISK-2 is not returned by df.

So now if I  cd /media/LOCAL\ DISK-2,  I get that directory.

But when I "ls", it is empty.

Remember that at this time df does not return DISK-2.

This morning, df returned DISK-2 and  cd /media/LOCAL\ DISK-2
ls
listed the same directories and files that are now shown as being in /media/LOCAL\DISK-1.

There have been no shutdowns or reboots since this morning.

If it  does not exist, how can I cd into it?  If I can cd into it, why does df not return it?

The answer to the last question is that it does not at this moment exist.  OK, then why is it listed under /media when I cd into /media?

Really, all of this is interesting but what I really want is to nail down the names of the two partitions so they do not change.

rsync does not like it when you have a none existing directory as a destination.  My experience with it has been that when this happens, it dumps the output to / and my / is not large enough for that kind of mistakes.

So what is the big deal?  Why not just type in the proper rsync command each time based on what df returns?

Because the only rsync I have got to work for /home is:

cd /media/usbdisk
sudo rsync --verbose  --progress --stats --compress --recursive --times --perms --links  --exclude=/media/LOCAL\ DISK-1/ --exclude=/media/LOCAL\ DISK-2/ --exclude=/media/usbdisk/  --exclude=/media/H_\ \ \ \ ~1/ --delete /home/   /media/usbdisk/linuxbackup

For a total hard drive backup including W2K, it is:
cd /media/LOCAL\DISK-1
sudo rsync --verbose  --progress --stats --compress --recursive --times --perms --links  --exclude=/media/LOCAL\ DISK-1/ --exclude=/media/LOCAL\ DISK-2/ --exclude=/media/H_\ \ \ \ ~1/ --exclude=/media/usbdisk/ --delete //   /media/LOCAL\ DISK-1/linuxbackupcomplete

Obviously when I enter either of the above commands and there is no DISK-2, but there is a DISK and a DISK-1, the results are entirely different than when there is no DISK but there is a DISK-1 and a DISK-2.

And entering the above manually every time according to what df returns is tedius and fraught with the possibility of erros.

So how do I fix it?

The partition /media/usbdisk never changes, but all of the instructions in that command must be correct to get what is expected.

Sorry to be so long, but I am trying to give enough information that no one has to ask a lot of questions.

Ubuntu 6.06 with all updates.

CSSJR

---

### Post by dcstar on 2006-10-22
[http://ubuntuforums.org/showthread.php?t=139535](http://ubuntuforums.org/showthread.php?t=139535)

---

### Post by cssutto on 2006-10-22
That link is interesting, but it does not resolve my problem.

I have only one external hard drive.  It is the partitions within that hard drive that are changing.

I can't make it change this morning.  I have re booted with the external drive off, with it on, shut down with it off and with it on, etc., and today it still shows disk and disk-1.

cd /media still lists LOCAL DISK-2

cd /media/LOCAL\DISK-2 still puts me in that directory, but "ls" shows it to be empty.

The link furnished does not address non-existant partitions.

I am beginning to think this is a partition problem.  I don't remember for certain, but I believe the Mastor was partitioned with Partition Magic before I installed linux.

I may have to repartition using linux.

CSSJR

---

