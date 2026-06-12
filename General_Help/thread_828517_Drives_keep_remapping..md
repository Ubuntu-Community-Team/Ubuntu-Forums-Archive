---
title: "Drives keep remapping."
date: 2008-06-13
forum: General Help
---

### Post by dbvanhorn on 2008-06-13
I have a system with several SATA drives, and several PATA drives.

On reboot, or after powering off, the drives keep remapping.

This morning, the partitions (according to gparted) were:

/dev/sdb1  74G drive (boots from here, mounts to /)
/dev/sda1  400G drive /disk1
/dev/sdc1  400G drive /disk2
/dev/sdd1  500G drive /disk3

Now I come home and fire up the system, and here's what I get:

/dev/sdc1 233G drive (wasn't seeing this drive earlier)
/dev/sdd1 74G
/dev/sde1 400G
/dev/sdf1 400G
/dev/sdg1 500G

Notice, NO drive is where it was this morning!

Under windows, this system never has these problems, or at least windows makes it all go away for me..  I've been running Ubuntu for about a year on this machine, having scrubbed Vista. 

1: How can I get the drives to stop changing?  My FSTAB is all wrong, and every time I change it, things are fine for a while, then Poof.


2: The problem I was looking at the last few days, the 500G drive is WAY slow, reporting 5.58M as opposed to the other drives at 42-68M

The 74G is ext3, the 400 and 500 drives are reiserfs, and the 230G is FAT32 (only used for common space with windows stuff)

---

### Post by VMC on 2008-06-13
Open a Terminal and type

```
sudo fdisk -l
```

Does the output stay the same. save the output somewhere and reboot and see if it's the same. It shouldn't change.

Edit: I wonder if your BIOS is doing somwthing with these. What kind of BIOS is it?

---

### Post by dbvanhorn on 2008-06-13
> **VMC said:**
> 
Does the output stay the same. save the output somewhere and reboot and see if it's the same. It shouldn't change.


Ok, I saved it, I'll see what happens next time.

> **VMC said:**
> 
Edit: I wonder if your BIOS is doing somwthing with these. What kind of BIOS is it?

It's possible, It's whatever came with the machine, I try not to mess with that stuff. 

On the slow HD though, why would one particular SATA drive be so amazingly slow?  I've tried it in EXT3, and REISER, results are the same or close enough not to matter.

This is my fstab from last time, the slow one is /sdd1.

# /dev/sdb1 /media/sdb1 reiserfs defaults,errors=remount-ro,noatime,auto,rw,dev,exec,suid,nouser,data=writeback 0 1
# /dev/sdc1 /media/sdc1 reiserfs defaults,errors=remount-ro,noatime,auto,rw,dev,exec,suid,nouser,data=writeback 0 1
# /dev/sdd1 /media/sdd1 reiserfs defaults,errors=remount-ro,noatime,auto,rw,dev,exec,suid,nouser,data=writeback 0 1


Now it's on /sdg1, and still just as slow.

---

### Post by VMC on 2008-06-13
Are you saying that fstab keeps changing?

---

### Post by dbvanhorn on 2008-06-14
No, FSTAB is the same, but the drives keep moving around, plus the one SATA drive is WAY slower than the others.

---

### Post by logos34 on 2008-06-14
WHy aren't you using UUIDs?  Are you running Dapper or something?  UUIDs (in fstab and /boot/grub/menu.lst) will solve the problem of musical drives (your disks are on different storage controllers which the bios scans differently each boot)

get the uuids with any of these commands

sudo blkid

sudo vol_id /dev/sd?

ls -l /dev/disk/by-uuid

---

### Post by dbvanhorn on 2008-06-14
> **logos34 said:**
> WHy aren't you using UUIDs?  Are you running Dapper or something?  UUIDs (in fstab and /boot/grub/menu.lst) will solve the problem of musical drives (your disks are on different storage controllers which the bios scans differently each boot)


Well, the answer to the first question might be "because I don't know any better"..  I'm running Hardy.   The boot drive has one of these in it's fstab line, but I didn't know what that was and one thing I've learned about linux is "if you don't know what it is, don't mess with it."

:)

Ok, I assume I can modify the other lines, adding these UUIDs like the boot drive's line.

---

### Post by VMC on 2008-06-14
> **dbvanhorn said:**
> 
This is my fstab from last time, the slow one is /sdd1.

# /dev/sdb1 /media/sdb1 reiserfs defaults,errors=remount-ro,noatime,auto,rw,dev,exec,suid,nouser,data=writeback 0 1
# /dev/sdc1 /media/sdc1 reiserfs defaults,errors=remount-ro,noatime,auto,rw,dev,exec,suid,nouser,data=writeback 0 1
# /dev/sdd1 /media/sdd1 reiserfs defaults,errors=remount-ro,noatime,auto,rw,dev,exec,suid,nouser,data=writeback 0 1
 Is this your fstab? It doesn't look right. Type this and show us the output:

```
cat /etc/fstab
```

---

