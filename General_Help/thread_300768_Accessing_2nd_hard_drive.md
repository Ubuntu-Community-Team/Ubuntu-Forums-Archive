---
title: "Accessing 2nd hard drive"
date: 2006-11-16
forum: General Help
---

### Post by Brian R. on 2006-11-16
New to ubuntu, have installed on an old machine with 2hdd and 1 cd and 1cdr. Installation finds all the drives, plus usb and card readers.
System runs but i cannot access 2hdd have followed instructions from community documents and are as follows.
sudo lshw -C disk
The 2hdd is called /dev/hdc
and the volume is called /dev/hdc1
sudo fdisk /dev/hdc
then d to delete old partitions
then n for a new partition
then p for primary and 1 for partition number
then w to write it to disk
after that sudo mke2fs -j /dev/hdc1 to format it
then sudo mkdir /backup
finaly sudo mount /dev/hdc1 /backup
I can then see the drive, permissions are r for all, but when i click the box to make it writable it tells me sorry permissions could not be changed. It also added a folder lost+found which tells me i am not the owner, so can do nothing.
Added the following line to the fstab
/dev/hdc1  /backup   ext3  defaults   0  0
also tried
/dev/hdc1  /backup   ext3 auto, user, rw  0  0
Great it mounts on boot but now permissions for drive are
r    w   x
r
r
All greyed out and still i cannot write to drive or the lost+found folder
WHAT AM I DOING WRONG

---

### Post by taurus on 2006-11-16
Your line in /etc/fstab should have been

```
/dev/hdc1 /backup ext3 defaults 0 1
```
Then at the prompt, change the permission of /backup with chmod...

```
sudo chmod -R 777 /backup
```

---

### Post by Brian R. on 2006-11-19
That worked perfectly thank you very much

---

### Post by ntense on 2006-11-21
that helps half of my problem... now i can write to the drive but what do i have to do to get an icon for it in "computer" where it shows all my other media like my cd and dvd drives? or does that not happen... i want to be able to easily access it. im still an uber noob myself so while the answer might be simple to others, i still need a little help

---

