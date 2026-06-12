---
title: "Mount Partitions on Ubuntu 8.04"
date: 2008-06-02
forum: General Help
---

### Post by ubtBaba on 2008-06-02
Hello,

I have a small problem with mounting partitions permanantly on Ubuntu 8.04.

Ubuntu 7.10 pre-mounted all available partitions for me in the past.  I have mounted dynamically through Nautilus, but I need it mounted at each restart.

If someone could please write the exact line I should write to my fstab.  I have been through countless forums and have failed.

Please give me a line for a ntfs partition with read-write access and give me a line for a ext3 partition with read-write access.

I will modify these lines to fit my disk structre.

Thanks

---

### Post by leito666 on 2008-06-02
sudo apt-get install disk-manager


Thats works great for me, it will add the lines necessary to the FSTAB.

---

### Post by TeoBigusGeekus on 2008-06-02
```
dev/Nameofdevice   /media/Mountpointofdevice   system   relatime   0   2
```

Nameofdevice: Can be found with
```
sudo fdisk -l
```

Mountpointofdevice: Can be found with
```
mount
```

system: Replace with ntfs of ext3

---

### Post by Nepherte on 2008-06-02
I suggest working with UUIDs of the disk, since in some cases the /dev/sdax can change.

For ntfs:
UUID=uuidnumber     mountpoint    ntfs-3g    defaults,locale=yourlocale.utf8   0    0

For ext3:
UUID=uuidnumber mountpoint ext3 relatime,errors=remount-ro 0 1

The options at the end of each line can vary, for more information on those options or automounting in general, see [https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

---

### Post by ubtBaba on 2008-06-03
:KS Thank You All :KS

I was able to succesfully able to mount with the following line,

/dev/sda9 /media/LinX ext3 relatime 0 2

Question #1
I am still trying to learn here, so please inform me what relatime and 0 2 means in this line; the rest I get.

Question #2
Also I want my username to be the only one to view this partition and modify; lets say my username is tuxMan.

Question #3
One user suggested I use UUID instead of the /dev/sda9 how can I find the UUID?

Question #4
Another user suggested that I install disk-manager, I tried to do this with apt-get & I also downloaded the package; only the latter installed but the application showed up in the system menu but it would not run.

Is this for Ubuntu 8.04 or a previous release?

Sorry for my long list of questions, I am still a newbie and clueless :confused:.

Thank you all for your patience and assistance you guys rock :guitar:.

---

### Post by ubtBaba on 2008-06-03
I guess my excitement was a little premature, I was able to mount the said partitions but don't have write access, anybody what I should add to fstab for write access to my user only; let's call this user name tuxMan.

Thanks

---

