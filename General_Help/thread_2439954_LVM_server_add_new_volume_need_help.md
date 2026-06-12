---
title: "LVM server add new volume need help"
date: 2020-04-03
forum: General Help
---

### Post by mhlxz on 2020-04-03
Hi guys,

I need help.
I have structure (attachment). Ubuntu 18.04

Web application XXX is running on dev/sda5 which is based on volume group srvomega01-vg

I added a new disk to the machine in Vmware but I have a problem how to add it to a volume group without any problems.

I need more space for this application.

I found few instructions but the didnt worked and I had internal server error. Please guys help how to do it step by step :(

---

### Post by TheFu on 2020-04-03
i need text please, not images.
LVM has 3 parts.
* PV
* VG
* LV
You'll need to add the other disk to a new PV.  Then add that PV to the existing VG.  Once added to the VG, then the LV(s) can use it.  But if the other disk isn't just virtual - if it is really a different physical disk - then perhaps using a new VG and separate LVs would be safer for the data.

Be very careful if you have a single LV that spans more than 1 physical disk.  You've been warned.

There are LVM tutorials on the web. Don't be to worried about finding an Ubuntu version.  LVM is LVM on linux.

if it was me, i'd create a new PV, new VG, then migrate the too-small LV over to the new disk, assuming the first disk is already split into multiple LVs for / , /home, /var, and swap with reasonable sizes already.
```
sudo pvs
sudo vgs
sudo lvs
lsblk -e 7 -o name,size,type,fstype,mountpoint
df -hT -x squashfs -x tmpfs -x devtmpfs
```
output would be highly useful.  Wrapped in code tags, like I’ve done.

---

### Post by mhlxz on 2020-04-04
The first disk has a 3 parts:
sda1 - linux/boot
sda2 - extended
sda5 - lvm and there is 
*srv01--root lvm
*srv01--swap lvm


[PHP]

Add new disk sdb to group srv01-vg

vgextend srv01-vg /dev/sdb

/etc/init.d/xendomains stop

pvmove /dev/sda5 /dev/sdb

vgreduce srv01-vg /dev/sda5

/etc/init.d/xendomains start

[/PHP]

What about the previous space?

It will work?
[https://www.youtube.com/watch?v=IygA1naVf8Q](https://www.youtube.com/watch?v=IygA1naVf8Q)

---

