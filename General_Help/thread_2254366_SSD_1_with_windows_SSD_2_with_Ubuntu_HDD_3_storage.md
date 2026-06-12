---
title: "SSD 1 with windows SSD 2 with Ubuntu HDD 3 storage for both? Will that work?"
date: 2014-11-26
forum: General Help
---

### Post by arron2 on 2014-11-26
Hi all

Quick(ish) question.... I have an SSD with Windows on which is my primary boot OS, always has been. I also have another SSD with Ubuntu on and working, installed today ( I just choose which to boot in the BIOS). I have a 3rd hard drive...actually another 5 storage HDDs, 2 of which are in a windows software RAID 0 ( just cause, why not complicate things further :P?). I use these drives already for storage in windows. Will switching between Windows and Ubuntu likely mess up corrupt or deny access to the files already on the HDDs ? Especially the RAID 0? they're internal SATA 2 HDDs. I was wondering if it might throw up some kind of permissions error, or read write error or anything? I have not yet plugged the storage drives back in cauussse it's a lotta data I'd rather not lose haha.

I'm only really experimenting with Ubuntu & testing as a new user at the moment so, if there is an obvious reason why this won't work or might cause data loss I suppose I'll just have to stick with windows :( I don't really need access to the storage drives in Linux I just need to know it won't mess existing data up basically. I know I could unplug them each time I use Ubuntu like I am now but ...that'd get old fast. 

Anyone got a similar set up and know it works?

---

### Post by oldfred on 2014-11-26
Generally you should not have issues.
But do not hibernate Windows.

You can add RAID drivers which are not normally in the Desktop install. And NTFS drivers are standard in Linux now.

But RAID 0 for data? And you mention data is valuable?
RAID 0 was used for boot drives when speed was required, like major compile tasks. Now SSD have replaced that need.
       Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

---

### Post by arron2 on 2014-11-27
Yeah you make a good point about the RAID 0 - I do a lot of 3D rendering and I didn't much like the idea of rendering to an SSD all the time so it was just a way around that. The data isn't irreplaceable on the raid 0 it'd just be a pain to replace;). 

Thanks for the reply and the tips on hibernation!

---

