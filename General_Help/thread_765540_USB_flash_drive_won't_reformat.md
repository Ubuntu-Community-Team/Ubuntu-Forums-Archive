---
title: "USB flash drive won't reformat"
date: 2008-04-24
forum: General Help
---

### Post by tjb891 on 2008-04-24
I have a sandisk 1 GB USB flash drive that won't completely reformat in Gparted. i put it in my sisters macbookpro with OSX 10.4 and she renamed it without my permission. Now It comes up as a personally identifiable name instead of the generic sandisc usb flash drive label it originally had. Since reformating the drive isn't getting rid of this does anyone else have any advise. Ubuntu won't let me change the name with rename.

---

### Post by Claus7 on 2008-07-05
Hello,

the first thing I would try would be to change the name back as it was from where I had changed it. Now if this isn't possible I would try to change its ownership with the following commands:

```
cd /dev
```
or 
```
cd /media
```

then there :
```
sudo chown your_user_name name_of_disk 
sudo chgrp your_user_name name_of_disk
```

Hope this helped,
Regards!

---

### Post by qpieus on 2008-07-05
It sounds like your sister changed the disk label. Reformatting does not change the disk label, that's why when you've reformatted the disk the label stayed the same. I believe gparted can change disk labels, though. I don't have gparted running here, so I can't tell you exactly how to do that in gparted. Just browse around in gparted and I'm sure you'll see an option to change the disk label. Make sure there's nothing on the disk you want to keep because I think relabeling the disk will wipe out the disk contents.

The command line tool fdisk can also change a disk's label, if you'd rather use a CL tool.

---

