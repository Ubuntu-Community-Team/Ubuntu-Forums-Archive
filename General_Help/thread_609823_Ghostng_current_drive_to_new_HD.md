---
title: "Ghostng current drive to new HD?"
date: 2007-11-11
forum: General Help
---

### Post by mikey12345 on 2007-11-11
My Ubuntu machine is running well but on a 40gig HD only.

I plan to buy a bigger HD and use GHOST and do a disk to disk copy.

Will this work or do i jeed to format the brand new drive first or something?


At work with windows this just works fine without doing anything.


If i do need to format - how do i do this and to what file system - not sure what mine is - whatever default ubuntu 7.10 is?

Thanks.

---

### Post by aidanr on 2007-11-11
Yes Ghost will work just fine, if you want a free alternative to Ghost try Partimage, the default Ubuntu filesystem is ext3.

---

### Post by mikey12345 on 2007-11-11
Thanks for the prompt reply.

So i won't need to mess around with formatting the drive. I can just buy from the shop and ghost on to it?

---

### Post by aidanr on 2007-11-11
Yes, I haven't used Norton Ghost before but it says it supports ext3, also there's [Ghost 4 Linux]("http://sourceforge.net/projects/g4l"), but using [Partimage]("http://www.partimage.org/") on the [SystemRescueCd]("http://www.sysresccd.org/Main_Page") worked a treat for me before and also I believe you can just boot the Ubuntu live cd and copy the files from one harddrive to the other though you may have to update /etc/fstab with the new uuid that way.

---

