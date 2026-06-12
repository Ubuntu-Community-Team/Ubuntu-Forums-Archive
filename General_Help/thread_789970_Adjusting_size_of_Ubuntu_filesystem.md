---
title: "Adjusting size of Ubuntu filesystem?"
date: 2008-05-11
forum: General Help
---

### Post by Arphahat on 2008-05-11
This past Friday, I installed Ubuntu using Wubi.  I wasn't sure how interested in it I was going to be, so I limited it to a small, 10GB installation.  Well, I am still examining and would like to have more room, but I have no idea how to access the area outside of the system.

I was going to just use my external harddrive, but I am trying to get some thing installed with Wine and it doesn't seem happy trying to run things off of that drive.

So, what is the trick?  How do I tell Ubuntu that it can use a larger chunk of the drive?  And, it would also be nice to be able to access the additional files outside of the filesystem, even after I expand it: is there a way to do that?

---

### Post by chorca on 2008-05-12
Well, as far as accessing the files outside of the linux partition, you're able to do that by going to the Places menu and clicking one of the items there that says "xxGB Media" (where xx is the size of the windows partition) and then you should be able to access what's on it by going to that icon.

As far as resizing the Ubuntu loop file, i'm not sure how you'd go about doing that, if you can. I suppose if you haven't gotten too far along in customizing and whatnot you could always reinstall, though someone might chime in on how to resize the loop file..

---

### Post by Arphahat on 2008-05-12
> **chorca said:**
> Well, as far as accessing the files outside of the linux partition, you're able to do that by going to the Places menu and clicking one of the items there that says "xxGB Media" (where xx is the size of the windows partition) and then you should be able to access what's on it by going to that icon.

As far as resizing the Ubuntu loop file, i'm not sure how you'd go about doing that, if you can. I suppose if you haven't gotten too far along in customizing and whatnot you could always reinstall, though someone might chime in on how to resize the loop file..

Well, I have two 120 GB drives, but only one is listed in Places, the one that does not have Ubuntu installed on it.  Is there a trick to get it to show up?

If there is a way to access the remainder of that drive, then it is not essential for me to have the loop file any bigger as I could just keep my files external to it.

---

### Post by chorca on 2008-05-12
One thing you can try is if the drives are NTFS formatted, install the ntfs-config utility. This will identify the NTFS-formatted partitions available to linux and let you configure how they're mounted. Give that a run and see if it's identified the partition but just not set up a mountpoint for it.

---

### Post by Arphahat on 2008-05-12
> **chorca said:**
> One thing you can try is if the drives are NTFS formatted, install the ntfs-config utility. This will identify the NTFS-formatted partitions available to linux and let you configure how they're mounted. Give that a run and see if it's identified the partition but just not set up a mountpoint for it.

ntfs-config did the trick.  Thanks!  Is there a way to add that mounted drive into "Places"?

---

### Post by chorca on 2008-05-13
You might be able to just drag it into the places menu, I'm not at home right now, so I can't test this theory though.

---

### Post by ago on 2008-05-14
[https://wiki.ubuntu.com/WubiGuide#head-c1b3095de0e43733f9336427bb90d7ef322de99c](https://wiki.ubuntu.com/WubiGuide#head-c1b3095de0e43733f9336427bb90d7ef322de99c)

---

