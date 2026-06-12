---
title: "How do I install Vista after installing Ubuntu 8.04?"
date: 2008-07-02
forum: General Help
---

### Post by eHobayyeb on 2008-07-02
Partitions details from Gparted:
> 
Partition **** Filesystem **** Mountpoint **** Size     **** Flags
/dev/sda1 **** ext3       **** /          **** 18.63GiB	**** boot
/dev/sda2 **** linux-swap ****            **** 2.80GiB
/dev/sda3 **** fat32      **** /windows   **** 53.10GiB


What can I do to correctly installs Vista Ultimate?

Thanks in advanced.
Mohammad

---

### Post by damis648 on 2008-07-02
Install it as normal, onto the partition when you would like. When you are done, you must reinstall grub to the MBR, as Vista will overwrite it. To do this, boot up with the liveCD and start a terminal. In terminal,
```
sudo grub
```
and you will be faced with a new prompt. Now:
```
find /boot/grub/stage1
```
and enter. This will return the partition on which Ubuntu/GRUB is located. Now:
```
root (hd0,0)
```
replacing "hd0,0" with what was returned by the previous command (this should be fine). Finally, run
```
install /dev/sda
```
replacing hda1 with the **boot disk** (NOT THE UBUNTU PARTITION!) (this should be fine).
Good Luck!

---

### Post by eHobayyeb on 2008-07-04
What is the grub??
How do I know which is the boot disk??

Thank you

---

### Post by VMC on 2008-07-04
> **eHobayyeb said:**
> What is the grub??
How do I know which is the boot disk??

Thank you

Grub will come later. You enter it through a Terminal. 

Vista needs a NTFS or unallocated partition to install though.

---

