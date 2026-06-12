---
title: "help building a second raid 5 volume"
date: 2007-12-07
forum: General Help
---

### Post by demiurgen on 2007-12-07
i have built a raid 5 volume, using the commands below, that i found on this guide:
[http://bfish.xaedalus.net/?p=188](http://bfish.xaedalus.net/?p=188)
```
sudo mdadm --create --verbose /dev/md0 --level=5 --raid-devices=8 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1 /dev/sdf1 /dev/sdg1 /dev/sdh1 /dev/sdi1    

sudo echo "DEVICE partitions" > /etc/mdadm/mdadm.conf
sudo mdadm --detail --scan >> /etc/mdadm/mdadm.conf

sudo mke2fs -j /dev/md0

/dev/md0 /var/media auto defaults 0 3
```
i need to make a second volume.
what do i need to change in the commands above to make that work???

---

### Post by fjgaude on 2007-12-07
I'm not sure what you mean by "second volume". You mean you wish to make another partition out of the drives that are in the present array? Or with new drives? If with new drives, all you do is change the md0 to md1 or some other number. Please explain a little more.

---

