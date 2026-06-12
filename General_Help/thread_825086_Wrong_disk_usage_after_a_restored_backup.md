---
title: "Wrong disk usage after a restored backup"
date: 2008-06-10
forum: General Help
---

### Post by Van Richten on 2008-06-10
First of all, sorry for the poor spelling and grammar, I'm not a native English speaker :D

I used to have a very old 20GB pata drive, and have my hardy heron installed on that, partitioned like this: a 12GB root partition and a 8GB /home partition.

Yesterday I upgraded my Hard Drives, and I get a cheaper 80GB sata drive, and made the partitions like this:
sda1 - 20GB for a primary ntfs partition, (because my mate doesn't want to use linux with me. So, XP for him, Ubuntu for me.)
sda5 - 512MB extended swap partition
sda6 - 43.71 ext3 partition for root.
sda7 - 10.31 ext3 partition for /home.

So I used this [Howto: Backup and restore your system]("http://ubuntuforums.org/showthread.php?t=35087") and copied my pata 12gb root partition to the sda6 partition and the pata 8gb home partition to the sda7.

After that, I updated the /boot/grub/menu.lst to look for root in sda5 instead hdc1 (old pata) and updated /etc/fstab to mount as home /dev/sda7 instead of /dev/hdc2.

I booted from my new hard drive, and everything looked fine, but now I'm having this weird problem:

When I made the backup, I was using 9gb of 12gb, therefore 75%. Now, in my new 43.17gb root partition, the disk usage still seems to be 75%, in every partition analyzer!

As a example, (Q)gparted shows sda6 is using 37.57gb (75% again), instead of only 9 gbs.

Same occurs with the hdc2 to sda7 partition moving.

Using the command du -sh in / and /home shows the right disk usage: 9gb for root and 3.57 for /home (which is another partition:sda7).

The problem is: Every program that I try to use to download files, like Deluge, Ktorrent, even Firefox doesn't allow me to download files to my /home partition, saying I don't enough disk space.

What Should I do? Is there any information I missed here?

Thank you all in advance :D

---

### Post by logos34 on 2008-06-10
Hmm.  I've seen this problem before a couple of times. I'd be interested in knowing the answer to it too.

---

### Post by Van Richten on 2008-06-10
Here are more information to help:

**fdisk -l**

Disk /dev/sda: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders
Units = cilinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xbacbbacb

Device Boot Start End Blocks System ID
/dev/sda1   *           1        2775    20978968+   7  HPFS or NTFS
/dev/sda2            2776       10337    57168720    5  Extended
/dev/sda5            2776        2845      529168+  82  Linux swap / Solaris
/dev/sda6            2846        8907    45828688+  83  Linux
/dev/sda7            8908       10337    10810768+  83  Linux

Disk /dev/hdc: 20.4 GB, 20411080704 bytes
255 heads, 63 sectors/track, 2481 cylinders
Units = cilinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe1ffe208


Device Boot Start End Blocks System ID
/dev/hdc1   *           1        1568    12594928+  83  Linux
/dev/hdc2            1569        2481     7333672+  83  Linux

**/boot/grub/menu.lst**

title           Ubuntu 8.04, kernel 2.6.24.7-omnislash4.5
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24.7-omnislash4.5 root=UUID=d24070b8-4da3-4ac6-92e4-4beaba3c1596 ro quiet splash locale=pt_BR
initrd          /boot/initrd.img-2.6.24.7-omnislash4.5
quiet

title           Ubuntu 8.04, kernel 2.6.24.7-omnislash4.5 SATA
root            (hd1,5)
kernel          /boot/vmlinuz-2.6.24.7-omnislash4.5 root=UUID=d24070b8-4da3-4ac6-92e4-4beaba3c1596 ro quiet splash locale=pt_BR
initrd          /boot/initrd.img-2.6.24.7-omnislash4.5
quiet

I can provide more information if you want :)

--------------------------------

Edit: another info (this seems to be more specific)

**df -h**
Sist. Arq.            Tam   Usad Disp  Uso% Montado em
/dev/sda6              12G  5,8G  5,6G  52% /
varrun                220M  104K  220M   1% /var/run
varlock               220M     0  220M   0% /var/lock
udev                  220M  100K  220M   1% /dev
devshm                220M     0  220M   0% /dev/shm
/dev/sda7              11G  3,5G  6,3G  36% /home
/dev/hdb               64M   64M     0 100% /media/HIREN'SBOOTCD8.2

Here, it says the partition in /dev/sda6/ have 12G, but it's incorrect. The real size is ~43GB.

---

