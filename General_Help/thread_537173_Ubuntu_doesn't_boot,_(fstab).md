---
title: "Ubuntu doesn't boot, (fstab??)"
date: 2007-08-28
forum: General Help
---

### Post by fusion.fake on 2007-08-28
hello, im fairly new to the linux-scene, and have it running for a few days. but i still didnt have any write rights to the old windows partition so i added -rw to the fstab file, like i read on the internet. but when i rebooted ubuntu didnt boot properly and i got an "internal error" saying xserver was shut down something,

so i looked for fstab (using livecd) but it was empty, totally empty 
i can see the partitions and hard drives with a command but i cant see/browse them while in ubuntu (w/livecd)

i dont have a backup of fstab (i know, i know) but how can i reconfigure this file and hopefully get my ubuntu running again ? is it reconfigurable? i think this is the problem because the file doesn't containg anything.

*i hope this is the right section for this if not please move.*

---

### Post by merlinus on 2007-08-28
You will have to boot from the live cd and manually mount your ubuntu partition.

```

sudo fdisk -l

```

will show which partition this is.

Then

```

sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/sda2 /media/ubuntu

```

(substitute the ubuntu partition from fdisk -l for sda2)


Then:

```

gksudo gedit /media/ubuntu/etc/fstab

```

-merlin

---

### Post by fusion.fake on 2007-08-28
i'll try asap. tx 4 the fast reply :)

---

### Post by fusion.fake on 2007-08-29
i tried what you told me but i'm still getting the same error message.. i seriously dont know what to do now:(

---

### Post by fusion.fake on 2007-08-29
anyone ? :confused:

---

### Post by confused57 on 2007-08-29
Were you able to open your /etc/fstab file, using merlinus' instructions?...here are more detailed instructions for mounting your root partition:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

If you are able to open your fstab file, for now place a # in front of your Window's entry, then try to boot your pc.

Is your Window's partition fat32 or ntfs?

---

### Post by fusion.fake on 2007-08-29
i tried the link u gave me and also tried the #. 
i just gave up and am reinstalling ubuntu :/

---

