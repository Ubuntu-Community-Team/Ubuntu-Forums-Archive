---
title: "trouble mounting drive 8.04"
date: 2008-06-23
forum: General Help
---

### Post by boynblack on 2008-06-23
hey all,

I'm having trouble mounting a hfs+ formated partition under Kubuntu 8.04.  The deal is I ran my g4 mac into the ground and decided to migrate back to a pc.  In so doing I have one SATA drive that has all my stuff on it and i'm having some issues mounting it.  I get the message "/dev/sdc7 does not exist" when i "sudo mount -t hfsplus /dev/sdc7 /backup.  I thought first that i didn't have hfsplus support installed in the kernal, but after checking the old config it shows i do.  So I really don't think it has much to do with it being a hfsplus partition.  I could be wrong however.  

any thoughts.

Caleb

---

### Post by sisco311 on 2008-06-23
Make sure you have the hfs and hfsplus modules loaded:
```
sudo modprobe hfs hfsplus
```
To load the modules at boot add this lines to the /etc/modules file:
> hfs
hfsplus

---

### Post by boynblack on 2008-06-23
i did do 
sudo modprobe hfsplus i didn't think to also modprobe hfs will give it a try

caleb

---

### Post by sisco311 on 2008-06-23
Also make sure you have selected the correct disk and partition.
In ubuntu sda, sdb, sdc device names can alter after a reboot.
In fstab you can use uuid to mount the partition.

```
sudo fdisk -l
```to list the partition tables.

---

### Post by boynblack on 2008-06-23
ok i got hfs and hfsplus loaded but when i fdisk -l

it tells me "doesn't contain a valid partition table"


grr

any ideas ?

---

