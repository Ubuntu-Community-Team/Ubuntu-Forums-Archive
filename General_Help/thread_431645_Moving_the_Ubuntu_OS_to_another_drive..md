---
title: "Moving the Ubuntu OS to another drive."
date: 2007-05-03
forum: General Help
---

### Post by Memocjro on 2007-05-03
Hi. I have the following problem.
On my system i have 2 HDD's one of 250Gb wich has WIndowsXP and 3 NTFS partitions and another HDD of 80Gb which has Ubuntu Fiesty 7.04 installed. 
Due to some circumstances i have to remove the hard disk drive which has the Ubuntu Fiesty from my system. 
Question is, how can i safely move my Ubuntu OS from one drive to another, without reinstalling this system.
Another question would be if it is possible somehow to resize one of the NTFS partitions in order to make space for the "incoming" OS.
Thanks.

---

### Post by kidders on 2007-05-04
Hi there,

Linux is happy to be moved around. The only thing you have to watch is that you tweak everything that needs to know what you've done. Off the top of my head...[LIST]
[*]You may need to tweak (or even reinstall) your bootloader.
[*]You will almost certainly have to alter /etc/fstab.[/LIST]...but it's worth thinking about this for a minute or two before hitting CTRL+ALT+Delete.

The basic procedure (which absolutely _**must**_ be done in a text-based environment, for safety) goes something like this...[LIST=1]
[*]Boot your PC using anything except the Linux installation you want to move. Any Linux boot CD will do, for instance.
[*]Drop to a console, and set up some destination disk partitions & create your new filesystems. Tools like **cfdisk** (for repartitioning) and **df** (a disk usage analyser) can be helpful.
[*]Mount the source and destination filesystems. It's very important to be able to guarantee that your original Linux install will work, in the event something goes badly wrong, so I would suggest forcing your old Ubuntu partitions to mount in read-only mode, to eliminate the possibility of accidents.
[*]Copy (ie _do not move_) your Ubuntu from one place to the other, being very careful to preserve permissions & ownership. Something like **sudo cp -dpR /mnt/old_ubuntu/* /mnt/new_ubuntu/** would be suitable.
[*]Make a list of what needs to be tweaked, and make any required changes. If you find yourself modifying or reinstalling Grub, don't forget to add a menu entry for your "old" Ubuntu, as well as your "new" one, so you can back yourself out of a mess easily.
[*]After a day or two, once you're sure everything's stable, you can dump your old Ubuntu partitions. If there's anything private (or commercially sensitive) on the old filesystems, you may want to shred them ... or at least overwrite large chunks of them with random data from /dev/urandom.[/LIST]Also, since you're going to the trouble of redesigning your filesystems & disk partitions, it might be worth asking yourself if you would like to do anything differently. For example, you might like to change the amount of virtual memory you allocate, or try out a new filesystem type.

> is it possible somehow to resize one of the NTFS partitions in order to make space for the "incoming" OS.Yes, it's possible, although personally I would do almost anything to avoid resizing partitions. It's quite a disaster-prone operation! If you find that you simply have no alternative, I would very strongly recommend:[LIST]
[*]Using a specialised partition manager. Partition Magic is one that many people know, but any reputable equivalent will do.
[*]Making backups (preferably byte-for-byte disk dumps) before doing anything irreversible.[/LIST]Moving operating systems around is conceptually straightforward, but can be very time-consuming ... which makes it very tempting to cut corners, and take risks. I hope you don't mind me sounding like someone's mother, but please go slow, and think (just for a moment) before doing something like writing out changes to a partition table.

I hope that helps. Reinstalling your Ubuntu from scratch would be a _real_ pain!

[COLOR=Silver][[SIZE=1]*[UAResolved]*[/SIZE]]("http://ubuntuforums.org/showthread.php?t=377083")[/COLOR]

---

### Post by Memocjro on 2007-05-04
This is the hard disk that has the Ubuntu OS on it. 
```
Disk /dev/sdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9824    78911248+  83  Linux
/dev/sdb2            9825       10011     1502077+   5  Extended
/dev/sdb5            9825       10011     1502046   82  Linux swap / Solaris
```
And this is the hard disk that i will have the copy of Ubuntu on it:
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6527    52428096    7  HPFS/NTFS
/dev/sda2            6528       29095   181277460    f  W95 Ext'd (LBA)
/dev/sda3           29096       30205     8916075   83  Linux
/dev/sda4           30206       30401     1574370   82  Linux swap / Solaris
/dev/sda5            6528       13054    52428096    7  HPFS/NTFS
/dev/sda6           13055       29095   128849301    7  HPFS/NTFS
```
I have managed to take 10GB of free space with a [Gparted LiveCD]("http://gparted.sourceforge.net/livecd.php"). Now the Ubuntu OS uses around 5,6 GB and i also plan to mount a NTFS partition (/dev/sda6 above) that will be used both from Linux and Windows, so i have made a 8.5Gb ext2 partition for ubuntu and 1.5Gb SWAP.
Resizing the NTFS partitions worked like a charm. I have even done a chkdsk from WinXP to make sure everything was ok.
I will try now to copy the files from one disc to another and see if i manage somehow to get it to boot. 
As far as i am aware, i am sure that i need to edit the /etc/fstab  file and also the /boot/grub/menu.lst file. As i remeber i have the grub installed on the /dev/sdb disk. 

What i am not sure about. Being given the above partitions table, wich one should i make an active partition? Right now the active partition is the one that has the WindowsXP OS installed on it. As long as i tryed seems that i can only have one active partition on same HDD.

---

### Post by psusi on 2007-05-04
The active partition flag is only meaningful to the windows MBR, so it doesn't matter which one is active.  You will need to install grub to sda's MBR after you finish the copy:

sudo grub
root (hd0,2)
setup (hd0)
exit

---

### Post by Memocjro on 2007-05-05
Thank you both for your support. I have successfully moved my Ubuntu OS to the first HDD and removed the second one from my System. Everything works fine. Had a little problem with GRUB, i modified the /etc/fstab file but didn't pay attention to the UUID numbers, I modified only the root locations but not the mount points.

---

### Post by kidders on 2007-05-05
Excellent news. :-)

---

