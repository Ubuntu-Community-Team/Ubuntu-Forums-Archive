---
title: "mdadm - cannot wipe old RAID5 array"
date: 2017-04-21
forum: General Help
---

### Post by MorneDJ on 2017-04-21
Spend a day on this, but as I am writing this I have a dd if=/dev/zero of=/dev/sdb bs=1M going, not caring about any data.

I want to create a new RAID5 array with spare disk, with the existing array being RAID5 where the one drive failed and I replaced that disk with a new drive. I decided to start afresh.

After battling the day yesterday, I reinstalled Ubuntu 16.2 server, installed mdadm and it again see's my old RAID5 array.

Stop array:
```
mdadm --stop /dev/md0
mdadm --remove /dev/md0
```

It tells me md0 was stopped. 

```
mdadm --zero-superblock /dev/sdb
```
Couldn't open /dev/sdb for write - not zeroing

I check mount and /proc/mdstat, md0 is not used.

Try:
```
sudo mdadm --create --verbose /dev/md0 --level=5 --raid-devices=3 /dev/sd[bcd]1 --spare-devices=1 /dev/sde1



```

mdadm: Screw you, device or resource busy (or something like that)

I have tried stopping this array numerous times, removing it, zeroing the superblock, restarting, even uninstalled mdadm and reinstalled. Tried yum. 

Please, what else can I do ?

PS: Yes, I did a search and followed:
[https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/5/html/Deployment_Guide/s2-raid-manage-removing.html](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/5/html/Deployment_Guide/s2-raid-manage-removing.html)

[https://www.digitalocean.com/community/tutorials/how-to-manage-raid-arrays-with-mdadm-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-manage-raid-arrays-with-mdadm-on-ubuntu-16-04)

[https://hardforum.com/threads/unable-to-zero-superblock.1227981/](https://hardforum.com/threads/unable-to-zero-superblock.1227981/)

[https://serverfault.com/questions/535231/mdadm-zero-superblock-on-disks-with-other-partitions-on-them](https://serverfault.com/questions/535231/mdadm-zero-superblock-on-disks-with-other-partitions-on-them)

[http://www.overclock.net/t/692183/removed-old-array-cant-make-new-w-mdadm](http://www.overclock.net/t/692183/removed-old-array-cant-make-new-w-mdadm)

[http://www.linuxquestions.org/questions/linux-newbie-8/raid-array-creations-fails-837744/](http://www.linuxquestions.org/questions/linux-newbie-8/raid-array-creations-fails-837744/)

[https://serverfault.com/questions/838295/unable-to-remove-the-software-raid-1-array-when-it-is-in-degraded-state](https://serverfault.com/questions/838295/unable-to-remove-the-software-raid-1-array-when-it-is-in-degraded-state)

etc etc (a lot of other pages, yet nothing)

---

