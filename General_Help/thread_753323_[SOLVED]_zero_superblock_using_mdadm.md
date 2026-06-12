---
title: "[SOLVED] zero superblock using mdadm"
date: 2008-04-12
forum: General Help
---

### Post by kroenecker on 2008-04-12
I get the following error on an unmounted drive when I try to zero the superblock.

 sudo mdadm --zero-superblock /dev/sda 

give me:

mdadm: Couldn't open /dev/sda for write - not zeroing

I'm using an old raid disk as my root in a new install, but the newest kernel seems to think that the root disk should be apart of a raid array...so I'm a bit confused about what I should try to do at the moment.

---

### Post by kroenecker on 2008-04-12
sudo dd if=/dev/zero of=/dev/sda bs=1b seek=488000000

the above finally worked to clear it out.

you can see progress by typing this in a different terminal:

sudo pkill -USR1 dd

---

### Post by kroenecker on 2008-04-12
Please note that the value I used for seek (on my 250 GB harddrive) is definitely NOT hitting only the superblock. So if you do this with a harddisk that has information on it you stand to lose data.

---

### Post by kroenecker on 2008-04-12
Just for my own record here is my fstab:

UUID=d944f29f-2089-4d64-b60a-fa99d68c3f02	/media/entertainment	ext3	1	2
UUID=ded0e895-bb4c-4583-9073-cad5e0c79bd4	/media/backup	ext3	1	2

I found the uuid by using 

sudo vol_id -u /dev/mdX

I'm not certain that the 1 and 2 are correct...

---

### Post by fjgaude on 2008-04-12
I would use 0 2 instead of 1 2.

---

### Post by ajo09 on 2008-04-16
O'K I've had this error solved too but the bitch were:

my old lvm2 configuration that have used my hard disk 
partition that I thought were free and tried to mdadm --zero-superblock "ing" ;(
 
 just apt-get remove lvm2 first and reboot 
 and you can mdadm your partitions again.

 N.B. -> if any old lvm2 configs were used for root system before,
 you should see to it  that your initrd file doesn't contain
 lvm2 scaning too ! If yes create a new initrd.
 just man initrd and see how!

 so love peace and rock and roll! (swing salsa flamenco usw..)

---

