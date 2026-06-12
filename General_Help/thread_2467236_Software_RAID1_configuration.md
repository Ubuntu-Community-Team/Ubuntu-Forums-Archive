---
title: "Software RAID1 configuration"
date: 2021-09-20
forum: General Help
---

### Post by jzelek95 on 2021-09-20
Hello,
i have four disks. Two of them are for system and swap, two of them are for / home and other data. 
The each pair sets are configured as software RAID1. The configuration was as shown below:


[https://pasteimg.com/image/screenshot-45.ck0TH](https://pasteimg.com/image/screenshot-45.ck0TH)



[https://pasteimg.com/image/screenshot-3.ck48s](https://pasteimg.com/image/screenshot-3.ck48s)



[https://pasteimg.com/image/screenshot-4.ckOa9](https://pasteimg.com/image/screenshot-4.ckOa9)



[https://pasteimg.com/image/screenshot-5.ckekC](https://pasteimg.com/image/screenshot-5.ckekC)


After installing the system, everything is fine, the problem is when one drive that has home folders is disconnected. 
The system is booting up but can't for the profile status:

[https://pasteimg.com/image/screenshot-10.ckv2J](https://pasteimg.com/image/screenshot-10.ckv2J)

fstab file:

[URL="https://pasteimg.com/image/screenshot-2.ck66Y"]https://pasteimg.com/image/screenshot-2.ck66Y


[/URL][URL="https://pasteimg.com/image/screenshot-2.ck66Y"]
[/URL]Does anyone have any suggestions why this configuration doesn't work?

The distribution is Zentyal 7.0 based on Ubuntu. It does not matter whether the system is virtual or installed on a physical machine. 
Reconnecting the drive doesn't always help[]("https://pasteimg.com/image/screenshot-2.ck66Y")

---

### Post by rsteinmetz70112 on 2021-09-20
Did you use mdadm to create the arrays or lvm2?
Did you use uuid to define the arrays or diid you use device names?
If you use device names and you disconnect one drive then the device names may change.

---

### Post by jzelek95 on 2021-09-20
I used mdadm and lvm manager to create array and LVM during installation process
In /etc/mdadm/mdadm.conf I have UUID of md device
I tried to use UUID of /dev/mapper/vgzentyal--1-home in fstab file but it doesnt change. After change fstab or mdadm.conf I used update-initramfs

---

### Post by rsteinmetz70112 on 2021-09-21
As I was asking about the UUIDs of the drives. See the link below:
[https://unix.stackexchange.com/questions/52321/using-uuids-with-mdadm](https://unix.stackexchange.com/questions/52321/using-uuids-with-mdadm)

What does ```
# cat /proc/mdstat
``` show when you have a drive disconnected?
I've always been able to disconnect a drive and have a RAID 1 array come up degraded. In fact that general how you replace a failed drive.

---

