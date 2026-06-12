---
title: "Floppy trouble: given UDI is not a mountable volume"
date: 2005-10-15
forum: General Help
---

### Post by temcat on 2005-10-15
Hi all,

how do I mount a floppy in Breezy? 

* When I try to do it in Nautilus, I get error "given UDI is not a mountable volume"

* When I try to manually mount it using 'sudo mount /media/floppy0',  mount answers 'You must specify filesystem type' (the same with '-t auto')

* When I try to manually mount it using 'sudo mount -t vfat /dev/fd0 /media/floppy0', I get '/dev/fd0 is not a valid block device'

The disk is readable in Windows XP, written in Linux (!). The floppy is in the drive.

`cat /etc/fstab | grep floppy' gives the following: 

/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

What gives?

---

### Post by temcat on 2005-10-15
Quick response to myself and all others having the same trouble. By issuing the following command:

pmount -d /dev/fd0

I was able to access the floppy and then mount/unmount it manually using 'mount' command. It is, however, still not mountable from Nautilus.

---

### Post by sphillips53 on 2005-10-15
I have had the same difficulty mounting the floppy drive in Breezy Badger 5.10 from inside Nautilus.  It appears that it is a problem with Nautilus.  
The command: 
mount /media/floppy0 
without a sudo command before it works fine for me and I put the command in a button on the panel to provide an easy work around to the malfunction in Nautilus.  Once it is mounted the floppy drive seems to work fine and it installs an icon on the Gnome destop that allows access to the contents of the floppy and an unmount command in its context menu.

Steve

---

### Post by joepotter on 2005-10-15
I have been complaining about this issue for a while now. It was some update a couple of weeks before Breezy went finale that killed off using the floppy at our site. We have 30 different boxes with 120 users and we can use no floppy devices as we did just a few weeks ago.

We can however use a USB floppy (a Lacie) just fine. We have major breakage here.

---

### Post by hva on 2005-10-17
[QUOTE=joepotter]I have been complaining about this issue for a while now. It was some update a couple of weeks before Breezy went finale that killed off using the floppy at our site. We have 30 different boxes with 120 users and we can use no floppy devices as we did just a few weeks ago.

We can however use a USB floppy (a Lacie) just fine. We have major breakage here.[/QUOTE]

i'm experiencing similar problems.
try the following:
1- sudo /etc/init.d/dbus restart
2 - gnome-volume-manager &
3 - killall gnome-panel
4 - killall nautilus

must be something wrong with hal or dbus or gnome-volume-manager...hope someone wiser than me can give more hints

---

### Post by paddyg on 2005-10-17
The following homemade solution has helped me get along with the floppy bug (Bugzilla Bug # 17562) in Breezy. Obviously, the bug is still there, but I don't care as I can mount my floppy via nautilus in a very tidy way (no terminal, formatting, killing anything).

1. I've changed the /dev/fd0 type from auto to vfat in /etc/fstab
2. Made a small bash file in my home dir:
	.mountfloppy (I like it hidden)
	chmod 700
3. Written the following lines in the file:
	pmount /dev/fd0;
	nautilus /media/floppy0
4. Made a launcher, which I added to the top panel, as follows:
	command: /home/myhome/.mountfloppy
	type: application

Of course, this is a per-user solution... well, if you've got hundreds of users, I know it's quite useless...

---

### Post by sphillips53 on 2005-11-03
See the thread:
> [http://www.ubuntuforums.org/showthread.php?t=85777](http://www.ubuntuforums.org/showthread.php?t=85777)
for instructions on how to update pmount from the dapper archive to fix this bug in breezy.

---

### Post by wreszamek on 2005-11-23
What helped me, change line in /etc/fstab from
```
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```
to 
```
/dev/fd0        /media/floppy0  vfat,ext2,msdos    rw,user,noauto  0       0
```
and then remount filesystems
```
sudo mount -a
```

---

### Post by hajk on 2005-12-04
Update the pmount package to version 0.9.6, it's in breezy-backports. This will solve the problems with mounting a floppy.

---

