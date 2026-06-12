---
title: "the volume uses the file system which is not supported by your system"
date: 2008-04-04
forum: General Help
---

### Post by arpanj2 on 2008-04-04
Hi

I was trying to automatically mount my NTFS partitions at startup using the following command

```

wget http://media.ubuntu-nl.org/scripts/diskmounter
sudo bash diskmounter
```

After this, whenever i try to open the partition, i get the above error message :-(

I have to mount the partitions using

```
sudo gparted
```

and then mount them...

Help plz...

Arpan

---

### Post by Maddmaxx on 2008-05-08
I have 10 IDE drives in my hardy heron system, and love the fact that 9 of the 10 drives are automatically mounted at boot time, but I can't get the one 320 GB drive to go, so I mount it the same way... Then I'm good 'til the next reboot. I think it may have something to do with the block size, since it's the only drive with a much larger block size than the rest. I still have not discovered a way to change the block size, other than to move all the files to another drive, and format the erroneous drive... By the way, I have tried using fsck to fix the drive and it appears to be healthy, any ideas?

Take care!

---

