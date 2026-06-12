---
title: "File system manual fixing"
date: 2007-08-01
forum: General Help
---

### Post by rutlandn on 2007-08-01
I have Ubuntu Feisty Fawn and Windows XP on my first hard drive and have also just reinstalled SuSE 10.2 on my 2nd. I now get a message on boot:
fsck.ext3: Unable to resolve 'UUID=5e5281ed-1d3b-4f6f-b9c4-a25524c76b67'
fsck.ext3: Unable to resolve 'UUID=94389eb7-c160-4e41-b981-4e8c1cb62b29'
plus a warning to fix the file system manually.
The desktop used to show the two partitions on my second drive, so presumably something can't see them.
Hitting 'exit' after the boot messages continues successful bot, but it's a bit irritating.
Any thoughts?

---

### Post by forestpixie on 2007-08-01
can you still see them if you open nautilus - I'm sure this is the same as I had a while ago.

Basically the UUID had changed for one of my drives and no longer matched the UUID fstab was looking for - once I'd changed fstab to suit it was fine.

Right click on the drive or partition n nautilus - volume tab and it'll show the UUID check it against the fstab entry.

Hope it's the same issue and this helps :)

Edit - that doesn't make much sense as such - but I did manage somehow to see them so I could get the UUID, might have been gparted?!

---

### Post by rutlandn on 2007-08-01
Thanks, but I'm not sure where I should be looking. I have an icon marked Filesystem which is not my Windows drive. Would this be it?

---

### Post by forestpixie on 2007-08-01
You can look there

Filesystem - then media 

or try computer on tool bar -

 I'm trying hard to remember for you how I got to volume properties - once I had them it was just a matter of changing the ID

---

### Post by forestpixie on 2007-08-01
> **rutlandn said:**
> :
fsck.ext3: Unable to resolve 'UUID=5e5281ed-1d3b-4f6f-b9c4-a25524c76b67'
fsck.ext3: Unable to resolve 'UUID=94389eb7-c160-4e41-b981-4e8c1cb62b29'

Of course if these are the new UUID's - and you know which relates to which partition you've got the information

check them in your fstab

- still can't remember where I found the number though :(

---

### Post by merlinus on 2007-08-01
```

blkid

```

-merlin

---

### Post by forestpixie on 2007-08-01
I've been looking at this

[https://bugs.launchpad.net/ubuntu/+bug/106209](https://bugs.launchpad.net/ubuntu/+bug/106209)

and I think how I sorted it was to edit fstab and comment out the changed partitions with #

gksudo gedit /etc/fstab

then rebooted and then was able to see the partitions in nautilus >computer

then edit fstab again and change the UUID for each 

There must be an easy way to find the UUID - but I haven't been here long and I'm afraid I don't know it :(

Edit - there it is :)

I'll put that on my list of things!

---

### Post by rutlandn on 2007-08-01
Thanks very much, guys.

Merlinus' blkid command did the trick and gave me the new UUIDs.  So it was just a question of  cut and paste into Forestpixie's gksudo gedit /etc/fstab.

Regards

---

