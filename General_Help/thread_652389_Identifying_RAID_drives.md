---
title: "Identifying RAID drives"
date: 2007-12-28
forum: General Help
---

### Post by gobuchul74 on 2007-12-28
I have a media server with two RAID arrays, all done via software RAID under Ubuntu.

One array is 6x500GB drives and the other array is 4x400GB drives.

Fortunately, I have not had any of the drives fail, but when I do, how do I identify the drive that has failed physically?

The system might report that drive SDB has failed, but how do I know which of the six 500GB drives is SDB?

I'll be upgrading the box with a new MB/CPU and replacing the array of 400Gb drives with 4x1TB drives. Is there something I can do during the build phase which will make identifying failed drives easier later?

Thanks,
Ed

---

### Post by psusi on 2007-12-28
Look in system->preferences->hardware information and find the drives and look at the serial numbers listed and compare them to the ones on the drives.

---

### Post by fjgaude on 2007-12-28
Wonderful... we take each drive out, mark it with a grease pencil as sda or whatever we found in System/Preferences/Hardware Information with its SN that we see on the manufacturer's sticker. Then make sure we can read such without having to take them out of their cage. Okay, thanks!

Don't need Mr. Kidder afterall.

---

