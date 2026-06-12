---
title: "reduce and clone lvm"
date: 2007-02-16
forum: General Help
---

### Post by jamesjrl on 2007-02-16
I have installed to a 70 gig partition using lvm
the amount actually in use is less than 10 gig

i would like to copy this system to a new drive, but am confused about this extra /boot partition and so want to see my new drive, with my old system booted and running before i destroy the data (and my only bootable OS) on my old one

i would also like to reduce the size allocated to my system in lvm
i have the system-config-lvm installed 
[http://www.ubuntuforums.org/showthread.php?t=216117&highlight=lvm+gui](http://www.ubuntuforums.org/showthread.php?t=216117&highlight=lvm+gui)
but cant resize my mounted OS so am hoping to take this opportunitry to reduce this size also.

i have come across guides to add drives, remove drives and move data in lvm... but i really want to see this copy boot and still have my old drive to go back to if it goes wrong.
is there a way to achieve what i want?

---

### Post by jamesjrl on 2007-02-18
the post [http://www.ubuntuforums.org/showthread.php?t=363263&highlight=lvm](http://www.ubuntuforums.org/showthread.php?t=363263&highlight=lvm)
helped me out here to some extent

using a lvm enabled bootable disc, looks like it should have helped me out here and should be useful for anyone wanting to do what i described.

although dd is still the only option to clone this drive.
i would advise resizing first, because dd want to blindly clone the empty parts of the partition as well.

unfortunately for me my volume is broken, and evms shows me /error/lvm2/UBUNTU segment  of size 500meg, which should not exist and is taking the uuid of my old drive.

i will have to do much more digging and tampering to get this fixed i think

---

