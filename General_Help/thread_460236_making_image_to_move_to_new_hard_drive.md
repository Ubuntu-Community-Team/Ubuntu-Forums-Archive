---
title: "making image to move to new hard drive"
date: 2007-05-31
forum: General Help
---

### Post by THEBIGEYE on 2007-05-31
i was just wondering if i make a back up of my drive if i will be able to some how install it on a new bigger drive as i dont want to have to install all my apps again it is just a small 4 gig drive but tis full and its all apps Many hours of work

---

### Post by swisscow on 2007-05-31
This can be done using the rescuecd. Download and burn the rescue CD  from

[HTML]http://www.sysresccd.org/Main_Page[/HTML]

and boot from this.

You can then use partimage (type this into the command line) to create an image of the partition you want to move. There's lots of different options but if it helps, what I do is this:

I have 4 partitions hda1=/ hda2=home hda3=swap hda4=storage (spare partition)

Once booted from the rescue cd i type
```
mkdir /mnt/backup
mount /dev/hda4 /mnt/backup
```

This makes a folder and mounts my storage partition there.

Then start partimage

```
partimage
```

Choose the partition you want to backup e.g. hda1, give it a location and filename to backup to, e.g. 

**/mnt/backup/name.000**

then accept the defaults and let it run - doesn't take very long.

Once finished reboot into Ubuntu, find where you saved the backup i.e. name.000, copy this to CD,DVD, memory stick, whatever depending on the sizeof the image, then install the new drive. You may have to do a basic install of Ubuntu, not sure but if you do make a note of the locations of each partition when you partition the drive.

Work out where you want your image to be restored to (/etc/fstab should help), then boot from the rescuecd, mount the cd drive (I don't do this but instructions are on the screen) and then run partimage and restore.

More and probably better instructions are available on the above web site and I believe psychocats has something to say on it too.

Good luck!

---

