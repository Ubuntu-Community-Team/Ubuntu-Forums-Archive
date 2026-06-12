---
title: "Trying to access Linux RAID member disk via live CD... unknown file system type?"
date: 2014-04-21
forum: General Help
---

### Post by aaron40 on 2014-04-21
Hope I can describe this properly as I'm just a casual Linux user!

Had a NAS that was running RAID1 and had a failed drive. Need to extract a folder from the GOOD drive but it isn't seen to be mounted when I boot to the Ubuntu live CD.

I was able to use other disks to *see* the drive but when I tried to mount it I received an 'unknown file system' error.

Used PartedMagic to inspect the drive & it does show used space so I know the data is there... just don't know how to access it from here!

I know it has to do with the MDADM command but everything I've tried has been unsucessful.

So, where do I go from here? I'm sure one of you guys would have this done in a snap but I'm lost! :P

Some pictures that might help:

[IMG]http://img.photobucket.com/albums/v245/aaron7/20140421_143636.jpg[/IMG]
[IMG]http://img.photobucket.com/albums/v245/aaron7/20140421_143736.jpg[/IMG]

---

### Post by SeijiSensei on 2014-04-21
So are we to understand that you removed the good drive from the NAS and installed it in a desktop PC?  Which drive is it in the pictures above?  
/dev/sda?  /dev/sdb?  If it's /dev/sda, can you mount any of the partitions?  
Software RAID1 disks in Linux can be accessed as individual devices, but whether you can extract one drive from a commercial NAS only the manufacturer probably knows.  Why not just replace the damaged drive with a new one and let the device rebuild the RAID array?

Rather than somewhat uninformative screenshots, let's try a few commands.  Open a terminal, then run:
```

sudo mkdir /media/sda1 /media/sda2 /media/sda3
sudo mount /dev/sda1 /media/sda1
sudo mount /dev/sda2 /media/sda2
sudo mount /dev/sda3 /media/sda3

```
Do any of those work, or do they all fail?

---

### Post by aaron40 on 2014-04-22
Trying to help a friend out who, unfortunately, doesn't know enough to answer some of these questions!

The NAS this drive was in had two drives and one had failed over a year ago. He's been running one drive in tehre this whole time!

I have the drive as the *only* HDD on a desktop PC to boot to this live CD.

Now, that picture I posted above with the table of drives is actually only one HDD. I'm not sure why it's listing it as so many different drives?

I have the drive at work, I'll try those commands a bit later and let you know. Thanks for the help! :D

---

### Post by SeijiSensei on 2014-04-22
Those are not separate drives. They are the partitions on the drive in question.

I still think buying a replacement drive for the NAS is the best solution if you want to return the device to its original state.

There is another drive, the WD device connected over USB.

---

