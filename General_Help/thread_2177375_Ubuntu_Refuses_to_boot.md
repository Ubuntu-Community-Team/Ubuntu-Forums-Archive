---
title: "Ubuntu Refuses to boot"
date: 2013-09-28
forum: General Help
---

### Post by chribuntu on 2013-09-28
So  I decided to triple boot Windows 7, Fedora 19, and Ubuntu 12.04. (All 64-bit). One day I booted up in Ubuntu and got an error. 
Any help would be appreciated.


[ATTACH=CONFIG]246559[/ATTACH]

---

### Post by chribuntu on 2013-09-28
BUMMMMMMMMMMMMMPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPp:(

---

### Post by oldfred on 2013-09-28
Please only bump once per 24 hours. We all are volunteers and may not be available immediately.

Often Fedora is installed with LVM. If you did not change to standard ext4 then you need LVM drivers in Ubuntu. Uusally LVM is for an entire drive but offers little advantage for just one partition.

In Ubuntu 
sudo apt-get install lvm2
 Then mount Fedora partition.
sudo update-grub

---

### Post by chribuntu on 2013-09-28
I used standard partitions for Fedora.

---

### Post by 64bitiso on 2013-09-28
Use Linux Mint; it doesn't spy on you.

---

