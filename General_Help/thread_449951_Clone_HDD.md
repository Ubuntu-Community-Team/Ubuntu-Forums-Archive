---
title: "Clone HDD"
date: 2007-05-20
forum: General Help
---

### Post by andytx on 2007-05-20
Hi all, 
I need to clone a old HDD to new HDD
I  have used , Ghost, Ghost4linux, CloneZilla, True Image. 
I did a Disk to Disk , and it's successfully Back and Restored, But When used New HDD to boot up, It's stayed at Ubuntu Logo while then it kick out.

Did anyone has successfully done to clone HDD? Please show me how to do? thank you

---

### Post by mbradlcu on 2007-05-21
yep, I use g4l all the time for intel macs and PC's. I wondering if you did a complete dump of the imaged drive or just /dev/{hda1,sda1}, also if you did a complete dump a couple things that could trip you up,, using a slightly smaller HD, or a different hardware topology,, ie, /dev/hda is now /dev/sda.
If you haven't already can you try the new drive in the same machine as the image was created from?

---

