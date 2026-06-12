---
title: "Expand partitions without losing data"
date: 2006-07-17
forum: General Help
---

### Post by Lunar_Lamp on 2006-07-17
I have a / and a /home ext3 partition setup, and ~20gb of unallocated space.  Can I boot up a livecd and somehow expand these paritions, without wiping the data already on them?  I.e. increase the / parition from 5gb to 7.5gb, and allocated the rest of 20gb to my /home partition?

---

### Post by reacocard on 2006-07-17
i assume it's something like this:

/ - 5 GB
/home - X GB
unallocated space

in this case, only /home can be expanded. you cannot move the /home partition forward to allow / more space.

---

### Post by Lunar_Lamp on 2006-07-17
So it depends upon where the space on the hard drive is?  

In a few days I should be able to access a large (250gb) usb hard drive.  Would it be a viable solution to do this:

'cp -a /dev/hdax /media/sda1/ROOT' 

'cp -a /dev/hdaX /media/sda1/HOME'

i.e. copy the two partitions to a usb hard drive, delete the two partitions, create new ones of the size I want, then copy the data back onto these new partions.  Is there a better way to do this (using dd?)?

---

### Post by reacocard on 2006-07-17
if you have a livecd lying around, there's an even better way. partimage: [http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html)

---

