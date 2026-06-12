---
title: "The system fails to recognize the order of the hard disks"
date: 2008-05-04
forum: General Help
---

### Post by Matiee on 2008-05-04
When switched from Gutsy to Hardy, I noticed that my disks are now always called **sd***x* instead of **hd***x*, even if they are on PATA.
I understand, from what I've read some time ago, that this is the normal behaviour of the libata drivers, but I don't know much about it.

A problem that I've noticed since the installation phase (because Hardy's live dvd has this problem too) is that sometimes (quite often indeed) Hardy fails to recognize the order of my disks as they are specified in the BIOS, and it calls my 3rd disk as **sda** instead of **sdc**.

When it happens from the live dvd I care little, but the problem persist once the system is installed and tries to boot:
disks' order is messed up, partitions aren't found or coulnd't be mounted because of wrong filesystem, I don't get home directory at all and I'm forced to shut down the computer and start it again.

This happens, let's say, 1 time out of 5, that is: it starts to be very frustrating... ](*,)

Has anyone else experienced my same problem?
Could someone please help someway?

Thank you.

---

### Post by Tosa on 2008-05-04
I don't have a solution (yet), just want to report the same problem in 7.10. I have two Sata and one Pata (boot) disks. Sometimes upon boot the order of disks is messed up and I have to mount them manually which is a bit annoying...

---

### Post by DaddyX3 on 2008-05-04
You will have to enter the UUID# data in the fstab file. This way they will never get mixed up on boot. 
Find you UUID: 
```
sudo blkid
```
Your fstab file then gets edited to utilize your UUID instead of a simple device call out name like: 
```
#old style entry
/dev/sda1 /media/sda1   defaults ext3 0  2
#new style entry - it would now become:
UUID=xxx.yyy.zzz  /media/sda1  defaults  ext3   0       2
```
Hope that helps.

---

### Post by Matiee on 2008-05-08
It worked. Thanks ;)

---

### Post by hyper_ch on 2008-05-08
only problem with this is swap as it changes its UUID (I think). I already opened a bug report [https://bugs.launchpad.net/ubuntu/+bug/224969](https://bugs.launchpad.net/ubuntu/+bug/224969) if you could also sign it ;)

---

