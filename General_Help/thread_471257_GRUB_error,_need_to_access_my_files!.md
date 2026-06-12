---
title: "GRUB error, need to access my files!"
date: 2007-06-11
forum: General Help
---

### Post by FleetAdmiral74 on 2007-06-11
I randomly got an Stage 1.5 error 24, i used gParted to check the fs, and now get error 15. I need to know how to fix this! help really appreciated.

---

### Post by weirdguille on 2007-06-11
[COLOR="DarkGreen"]Hi.  I don't really understand your problem, but... well, if what you need is to access your files, why don't you use a liveCD while you manage to solve your problem?
I am unable to log into my Ubuntu as well, but am using Puppy Linux (it lets you mount easily almost any drive) meanwhile.
Check it out.  It's also very light.[/COLOR]

---

### Post by merlinus on 2007-06-11
Boot fropm any live cd.  Open a terminal and enter:

sudo grub
find boot/grub/stage1
root (hd0,7)
setup (hd0)
quit

Substitute your results from find in the next two steps.

Also, look at and compare the entries in /etc/fstab and /boot/grub/menu.lst

-merlin

---

### Post by FleetAdmiral74 on 2007-06-11
> **merlinus said:**
> Boot fropm any live cd.  Open a terminal and enter:

sudo grub
find boot/grub/stage1
root (hd0,7)
setup (hd0)
quit

Substitute your results from find in the next two steps.

Also, look at and compare the entries in /etc/fstab and /boot/grub/menu.lst

-merlin

I am trying to get what you are saying. So after the find command I sub results I found  for the root and setup part? And after I compare the two logs mentioned, what do I do with them? just copy one and make sure the other matches?

---

### Post by merlinus on 2007-06-11
After the grub "quit" command, reboot from your hard drive (not cd) and see what happens.

If this does not fix your problem, then post the contents of those two files.

Also, the results of:

```

sudo fdisk -l
blkid

```

(l is a lowercase L)

It may be that grub is not finding the linux kernels.

-merlin

---

### Post by FleetAdmiral74 on 2007-06-11
```
grub> find boot/grub/stage1

Error 15: File not found

grub> root (hd0,7)

Error 22: No such partition

grub> setup (hd0)

Error 12: Invalid device requested

grub> 

```

I have not restarted yet, because none of the above steps seemed to work :(

---

### Post by merlinus on 2007-06-11
Looks like grub is not being found.

Please post the output of the two terminal commands, and contents of the two files.

-merlin

---

### Post by FleetAdmiral74 on 2007-06-11
Oh, just fyi. I should have two HDs, one with WIndows all NTFS. The other should have a 93gig ex2 or 3, some swap, and unallocated. 

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9963    80027766    7  HPFS/NTFS

Disk /dev/hdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       12158    97659103+  83  Linux
/dev/hdb2           12159       12220      498015   82  Linux swap / Solaris
/dev/hdb3           12221       30401   146038882+   f  W95 Ext'd (LBA)
/dev/hdb5           12221       30401   146038851   83  Linux

Disk /dev/sda: 512 MB, 512753664 bytes
16 heads, 62 sectors/track, 1009 cylinders
Units = cylinders of 992 * 512 = 507904 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1009      500433    b  W95 FAT32

```

```
ubuntu@ubuntu:~$ blkid
/dev/sda1: LABEL="DATA" UUID="24FC-0AB8" TYPE="vfat" 

```

This is the jumpdrive I have plugged in I believe. Thanks for sticking with this, I will be right back. Have to work, will post the files soon.

---

### Post by ryanVickers on 2007-06-11
So, is it unbootable?

In that case, first make sure grub is configured correctly - I recommend this thing that I don't remember the name of, although I just used it 10 minutes ago :p

Look up super grub disk or super grub tool or something like that and you'll find it - It's really good!  Then, make sure in your fstab, mtab, and menu.lst files all are configured properly!

---

### Post by koshari on 2007-06-11
wont he need to mount the hard drive with the grub directory on it for find to work?

---

### Post by merlinus on 2007-06-11
SuperGrub info at:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

-merlin

---

### Post by logos34 on 2007-06-11
> grub> find boot/grub/stage1

you left out a '/'.  Should be:

grub> **find /boot/grub/stage1**

---

### Post by merlinus on 2007-06-11
Good eyes!

-merlin

---

### Post by ryanVickers on 2007-06-11
> 
wont he need to mount the hard drive with the grub directory on it for find to work?
**What!?** :p

If you mean need use of the cd drive or something, I just burned it on another computer while I was ion the live CD - samba! (to another linux machine, eisier than the linux sharing!)

---

### Post by FleetAdmiral74 on 2007-06-11
Hmm, no luck.

```
grub> find /boot/grub/stage1

Error 15: File not found

```

Checking out that Super Grub thing, will update later. Any way I can save these temps settings I have used since booting to the usb so I dont need to reenter stuff? 

And lastly, did you want me to find those files in the Filesystem folder, or in one of the other harddrives folders...cause I can access the Windows HD, but only get a lost+found folder for the linux hd.

---

### Post by merlinus on 2007-06-11
Try SuperGrub first.

The files I referred to are on your ubuntu partition, which you will have to mount manually via a terminal command whilst running the live cd.

First things first....

-merlin

---

### Post by FleetAdmiral74 on 2007-06-11
Hehe, a terminal command you say? enlighten me o linux guru!

edit: yeah, ill try that super program...

---

### Post by merlinus on 2007-06-11
The same way you entered the find grub command.  In a terminal....sometimes called a CLI (command line interface).

As in:

Applications/Accessories/Terminal

-merlin

---

### Post by FleetAdmiral74 on 2007-06-11
Sorry, I meant the actual command to do the mount procedure :)

edit, I right clicked the icon in Computer and mounted, same thing. Just lost and found. I am thinking backing up the data and just reinstalling will be easier...how would I go about doing that?

---

### Post by merlinus on 2007-06-11
mount -t [type of file system: ntfs -> NTFS, vfat -> FAT, ext3 -> Linux] /dev/sdaX /media/your_mount_directory

You need to make the mount directory first:
```

sudo mkdir /media/sdaX

```
for example, where X is a number.

The results of sudo fdisk -l will help.

-merlin

---

### Post by FleetAdmiral74 on 2007-06-12
Does not recognize the fs, idk. Again, thanks for sticking with this. I know its annoying to read all this!

sudo fdisk -lubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9963    80027766    7  HPFS/NTFS

Disk /dev/hdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       12158    97659103+  83  Linux
/dev/hdb2           12159       12220      498015   82  Linux swap / Solaris
/dev/hdb3           12221       30401   146038882+   f  W95 Ext'd (LBA)
/dev/hdb5           12221       30401   146038851   83  Linux

Disk /dev/sda: 512 MB, 512753664 bytes
16 heads, 62 sectors/track, 1009 cylinders
Units = cylinders of 992 * 512 = 507904 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1009      500433    b  W95 FAT32
ubuntu@ubuntu:~$ sudo mkdir /media/hdb1
ubuntu@ubuntu:~$ mount -t [Linux /dev/hdb1 /media/hdb1]
mount: only root can do that
ubuntu@ubuntu:~$ sudo mount -t [Linux /dev/hdb1 /media/hdb1]
mount: mount point /media/hdb1] does not exist
ubuntu@ubuntu:~$ sudo mount -t [Linux] /dev/hdb1 /media/hdb1
mount: unknown filesystem type '[Linux]'
ubuntu@ubuntu:~$

---

### Post by merlinus on 2007-06-12
Try this:
```

sudo mount -t ext3 /dev/hdb1 /media/hdb1

```
Then try the find grub commands.  They might wind up as (hd1,0), which would be your second hard drive, first partition.

Remember to substitute your results in root and setup.

```

sudo grub
find /boot/grub/stage1
root (hd0,7)
setup (hd0)
quit

```

-merlin

---

### Post by FleetAdmiral74 on 2007-06-12
```
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/hdb1 /media/hdb1
mount: wrong fs type, bad option, bad superblock on /dev/hdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

also,
grub> find /boot/grub/stage1

Error 15: File not found

Figure I had better fix this before the other commands, so I'm calling it a night. Will work on this tomorrow, see ya then Merlin.

---

### Post by merlinus on 2007-06-12
In the morning, please give this a try:
```

sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/hdb1 /media/ubuntu

```
I'm off to bed now...

-merlin

---

### Post by FleetAdmiral74 on 2007-06-12
Ok maybe I am not asleep yet  :)

```
mount: /dev/hdb1 already mounted or /media/ubuntu busy
mount: according to mtab, /dev/hdb1 is mounted on /media/hdb1
ubuntu@ubuntu:~$ 

```

Seems to be mounted from earlier, but in that media folder still only lost and found. I hope the files are still there...

---

### Post by FleetAdmiral74 on 2007-06-12
Stick with me here!   :)

Just need to grab the files so I can reinstall easily.

---

### Post by ryanVickers on 2007-06-12
If you've givin up hope of a recovery, then the next step would be to boot from the live CD, then copy your files to somewhere other than the partition that will be formated durring the re-install.

What version of live CD are you using?  I would recommend the 7.04 or 6.06 one, but definitly not the 6.1!

---

### Post by FleetAdmiral74 on 2007-06-12
> **ryanVickers said:**
> If you've givin up hope of a recovery, then the next step would be to boot from the live CD, then copy your files to somewhere other than the partition that will be formated durring the re-install.

What version of live CD are you using?  I would recommend the 7.04 or 6.06 one, but definitly not the 6.1!

I'm just going to assume you have not read the rest of the thread, thats alright its pretty long.  ;)

I have the 7.04 live cd (using now). I need to mount the partition or whatever to access the files, once I have them I am good to go. The rest of this thread pretty much shows my progress, or lack thereof.

---

### Post by FleetAdmiral74 on 2007-06-12
I followed the instructions at [http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

I think this worked...the only thing is there are thousands of folders! all my stuff seems to be here though, its just a matter of finding it all...this will take forever ;)

damn, there are all #2524 and ect. Don't have their names! I cant possible go through all of this and find all my stuff! but its there! haha this is frustrating.

---

### Post by merlinus on 2007-06-12
Before throwing in the towel, download the Knoppix live cd.  Booting from it may well let you access the files you are wanting from hb1.

[http://www.knopper.net/knoppix/index-en.html](http://www.knopper.net/knoppix/index-en.html)

-merlin

---

### Post by FleetAdmiral74 on 2007-06-12
Would it just give me the same cryptic file names though, and would I have to go through the trouble of figuring out how to mount it and what not? Cause if it is easier for my to just figure out how to find my files, i will do that. I wonder if there is some filter or something...idk.

---

### Post by ryanVickers on 2007-06-12
> 
I think this worked...the only thing is there are thousands of folders! all my stuff seems to be here though, its just a matter of finding it all...this will take forever

damn, there are all #2524 and ect. Don't have their names! I cant possible go through all of this and find all my stuff! but its there! haha this is frustrating.

Is everything intact, just lost in the maze of folders, or is it scattered all over!  If it's pred like bird sead all of your files across the home folder, I wouldn't settle for that!  Oh, have you heard of something called a "search" :p  You could just enter *.mp3 or *.jpg or anything and it'll pick out certain folders with those contents!

---

### Post by merlinus on 2007-06-12
IIRC, Knoppix will automatically mount your various drives.

As for filenames, though, they will not change.

It might be easier to simply find the most important folders and backup those files, rather than drive yourself crazy.

When you re-install ubuntu, make a separate partition for /home.  Your preferences and configuration files for the various apps live there, and you can also create folders in which to store your data.

Then it will be easy to backup what you need periodically.

Good luck!

-merlin

---

### Post by FleetAdmiral74 on 2007-06-12
hehe, simply find the files eh? what was the simple part of looking through thousands of files :)

Eh, Ill stop whining. I just really, really wanted to get me essay, but I did a search and could not find it. Some names are intact it seems if there were in a subfolder, but most are random.

---

