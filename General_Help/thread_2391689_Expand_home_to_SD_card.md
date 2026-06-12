---
title: "Expand /home to SD card"
date: 2018-05-12
forum: General Help
---

### Post by rouvenster on 2018-05-12
Hello, 
I am running Kubuntu 17.10 on a 32gb Atom tablet and wish to expand my /Home partition with a 64GB SD card.
Is there a simple way to proceed ? As for now my system doesn't automatically mount my SD card (on the SD card reader) at boot so I hope there won't be any complications if I use it as a /home partition...
Any ideas ?
Thanks

[edit]
Thinking about it, I have a better option, which is a portable 256GB SSD USB Type-C that I can connect to my USB-3 port (less wear out problems). But I still doesn't know how to expand the partition to it...

---

### Post by dino99 on 2018-05-12
Some related discussions: [https://askubuntu.com/questions/95391/how-do-i-mount-an-sd-card](https://askubuntu.com/questions/95391/how-do-i-mount-an-sd-card)

When the automatic mount  will be resolved, then you need to know  its location: run 'sudo blkid'
Then insert the mount point into /etc/fstab .
But i've no clue about how that will be named after each reboot: maybe you will need to set a 'label' then use that 'label' into fstab (instead of the default uuid, which might change with each reboot)
[https://www.cyberciti.biz/faq/rhel-centos-debian-fedora-mount-partition-label/](https://www.cyberciti.biz/faq/rhel-centos-debian-fedora-mount-partition-label/)

---

### Post by rouvenster on 2018-05-12
I don't understand how I should add it to the /etc/fstab .
I made it as /home but now it is confused as there is already a /home (from my HDD).
Here is my /etc/fstab :
 

UUID=8418-5DC9                                                   /boot/efi vfat    umask=0077              0       1
UUID=034b4781-4b59-44b9-ab20-27f454069c80        /           ext4    errors=remount-ro       0       $
UUID=7b14180b-6c59-48cb-866f-bf629ebe13a0         /home   ext4    defaults                     0       2
UUID=9fc4c9a0-fcd5-4f5d-bfc3-4fbacc0df8c5            /home   ext4    defaults                     0       0


Last entry is my new partition I want to add to /Home

---

### Post by dino99 on 2018-05-12
the external /home can be named as you wish (ex: /hom)
can be set as: UUID=9fc4c9a0-fcd5-4f5d-bfc3-4fbacc0df8c5 /hom ext4 defaults 0 2

---

### Post by yancek on 2018-05-12
What you have done is to create two separate mount points for two physically different locations (shown by UUID) so you will probably see one or the other.  You could probably do this with LVM which I am not really familiar with or you could do as suggested and have different mount points for it.  Or just use the mount point for the new, larger disk.

---

### Post by oldfred on 2018-05-12
I would not use it as /home, but make it your data partition and link folders into /home. I have /home inside / on SSD and /mnt/data on HDD. from:
 sudo du -hc --max-depth=1 

 130G    ./mnt
337M    ./home 

My /home is small as it only has the hidden user settings. I even move some large normally hidden folders like my Firefox & Thunderbird profiles.

You have to create mount point, give yourself ownership & permissions, and mount data partition in fstab by UUID. Then you can copy /home's folders like Documents, Music, etc into data partition and link those folders back into /home. Be sure to have good backups before any changes.
Details:
       
 [http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)

It used to be that when booting if an entry in fstab other than / would give an error, then after timeout would still boot. Now it seems that many have reported it just does not boot. So never remove memory card.

---

