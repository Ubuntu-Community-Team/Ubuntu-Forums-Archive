---
title: "hardware detection (i do not have 2 cd drives)"
date: 2008-02-08
forum: General Help
---

### Post by toucansam99 on 2008-02-08
ok so I'm trying to run the envy script so my nvidia gforce 8800 gts card will work, and it needs the install disk.  no problem, i stick it in the drive.  but it can't find it in /cdrom/.  this is because /cdrom/ is a shortcut to /media/cdrom0

cdrom0 is empty

the cd is in cdrom1, for some reason.  So i can either edit the shortcut, or somehow make ubuntu change the current cdrom choice.  and i know how to do neither (wel, i tried editing the shortcut, but even sudo didn't work).

It would be great for ubuntu to realize that there is only one cdrom.

how do i fix this?

---

### Post by dcstar on 2008-02-09
> **toucansam99 said:**
> ok so I'm trying to run the envy script so my nvidia gforce 8800 gts card will work, and it needs the install disk.  no problem, i stick it in the drive.  but it can't find it in /cdrom/.  this is because /cdrom/ is a shortcut to /media/cdrom0

cdrom0 is empty

the cd is in cdrom1, for some reason.  So i can either edit the shortcut, or somehow make ubuntu change the current cdrom choice.  and i know how to do neither (wel, i tried editing the shortcut, but even sudo didn't work).

It would be great for ubuntu to realize that there is only one cdrom.

how do i fix this?

Check the jumper settings on your CDROM, if it is the only thing on the IDE channel, make sure it is set to Master and not Slave.

---

### Post by pointone on 2008-02-09
Envy is looking for the CD ROM because it's enabled in your apt sources.list. Edit /etc/apt/sources.list and remove or comment the lines related to the CD ROM.

You can change the shortcut by using the following commands:

```
sudo rm /media/cdrom
sudo ln -s /media/cdrom1 /media/cdrom
```

---

### Post by toucansam99 on 2008-02-09
I want the cd rom to be an option, but a working option ;)   I managed to fix this by mounting at cdrom0 as well. (so i had two mounts of the same cd ha).  Its on master, I'm not sure why it thinks there's two.

---

