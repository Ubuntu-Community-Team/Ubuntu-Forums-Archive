---
title: "disable fsck for fat32 partition on init boot"
date: 2007-10-31
forum: General Help
---

### Post by suvx on 2007-10-31
Hi all!
I migrated from suse to gutsy. the gutsy installation finds some corruption on a fat32 when it does its initial fsck on ALL partitions, causing a hang without error msg-so no gutsy for me so far:(

is there a way to disable fsck via boot flag, or what would you suggest?

TIA,

Felix.

---

### Post by taurus on 2007-10-31
Edit /etc/fstab and replace the last two numbers for your vfat partition with 0 0.

---

### Post by suvx on 2007-10-31
taurus,
i cant edit fstab because the system wont boot after installation.
What can I do?
Regards,
F.

---

### Post by taurus on 2007-10-31
Can you boot your machine with the LiveCD?  Then, you can mount your harddrive where / is and edit /etc/fstab from your LiveCD.

Open a terminal (while in LiveCD) and post the output of this command.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by suvx on 2007-10-31
taurus,

oh yeah good idea-i can do that - in the fstab i just 0 the check column, right?

how is the root partition to be mounted-actually i dont know how to mount ext3 manually.

the device should be 

/dev/sda2 

Ill find out....

Thank you very much for being so helpfull!!!

All the best & happy halloween,

    Felix.

---

### Post by taurus on 2007-10-31
```
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/sda2 /mnt/ubuntu
gksudo gedit /mnt/ubuntu/etc/fstab
```
and make sure the last two numbers are 0's.  Save it.  Then unmount the harddrive and reboot.

```
sudo umount /mnt/ubuntu
```
See if your machine boots from the harddrive this time.

---

### Post by suvx on 2007-10-31
taurus, 
yes that will do-i will check tomorow-its my office machine....

HAND,

felix.

---

