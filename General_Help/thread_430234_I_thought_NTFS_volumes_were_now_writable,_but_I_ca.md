---
title: "I thought NTFS volumes were now writable, but I can't. [Resolved]"
date: 2007-05-01
forum: General Help
---

### Post by mjpatey on 2007-05-01
I read that in Feisty, we should be able to write to our NTFS volumes.  I've been trying to save files to my existing Windows partition, but it says there's no space free (which is wrong; there's about 7 GB free).  Digging deeper, it seems I don't have permission to write to it.

So I try to change the permissions for the volume to allow me to write to it (by opening Nautilus as root, using gksudo nautilus), but even in that mode I can't seem to change permissions, because I'm still not the owner of the volume.

Any idea what I'm missing?

Thanks for any help you may have!

-Mark

---

### Post by mjitkop on 2007-05-01
You have to install the "ntfs-3g" package from Add/Remove Programs: click on "Applications" in the upper left corner and then "Add/Remove...".

Look at my screen shot.

---

### Post by aysiu on 2007-05-01
Follow these instructions (screenshots included):
[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)

---

### Post by TransitMan on 2007-05-01
Go to [www.getautomatix.com]("http://www.getautomatix.com") and install Automatix2. 
That proggy has a list of of instalable programs, including the one to allow read/write in NTFS volumes. I used it to setup my Feisty OS and so far it has not given me any problems.

---

### Post by mjpatey on 2007-05-01
mjitkop and aysiu-

Right!  You know, I actually knew that... I just thought it was installed by default.  Thanks for the tip!  It works beautifully now.  :-)

TransitMan-

Thanks also for your info.  I've been trying to challenge myself on this install not to use Automatix... so far so good!  But thanks just the same.  :-)

-Mark

---

