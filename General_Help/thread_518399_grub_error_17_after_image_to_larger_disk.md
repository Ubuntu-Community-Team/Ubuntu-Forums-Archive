---
title: "grub error 17 after image to larger disk"
date: 2007-08-05
forum: General Help
---

### Post by ageilers on 2007-08-05
I made an image of my 30GB hard drive and dropped it on a 60GB hard drive (IBM ThinkPad T23) with ghost. When I went to boot, all I got was GRUB and a flashing cursor. I was able to fix that by using Super Grub boot disk. I can boot into my Windows partition, but when I boot into Feisty, I get an error 17 code. I cannot boot into any kernel option. Ahhhh! Any help is greatly appreciated.

---

### Post by ageilers on 2007-08-06
Booted with Gparted and did a check on the partiton, came up ok. I was able to boot to the Live CD and mount my root partition. Not really sure what to do now. I do not want to reinstall Kubuntu.

---

### Post by confused57 on 2007-08-06
> **ageilers said:**
> Booted with Gparted and did a check on the partiton, came up ok. I was able to boot to the Live CD and mount my root partition. Not really sure what to do now. I do not want to reinstall Kubuntu.
It's possible that imaging your install could have changed the UUID's of your partitions.  Boot the live cd, run the command:
```
blkid
```

Then mount your root partition:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

Compare the UUID's listed in blkid with the UUID's in your /etc/fstab and /boot/grub/menu.lst.

---

