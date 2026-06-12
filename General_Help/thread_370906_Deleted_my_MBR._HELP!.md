---
title: "Deleted my MBR. HELP!"
date: 2007-02-26
forum: General Help
---

### Post by bash on 2007-02-26
I was testing out "Boot 'n' Nuke", coz the screen of a laptop i had broke. So i wanted to shrad all the content on it. But since I wanted to know what keys I have to press to start the shredding I took a look at the BnN CD on my main machine. By accident I started the shradding and I killed bout 0.22% of ma HDD. Now if I try to normally start, no grub appears. Worse than that, im currently surfing of the Live CD. When I checked the HDD in gparted the whole thing was shown as "unallocated". So I can't even acces my data. 

Any brilliant ideas on how to get myself out of this mess. I wouldn't even be very bothered if I had to reinstall Edgy as long as I could have copied of my important data to an external harddrive. But since that is now not possible my main concern is now how to manage to get access to my data, Or might something like a recovery program work. Just know them from Windows. Any good programs that do that for linux. Btw my Filesystem was ext3. 

Help would be very appreciated.
Thanks

---

### Post by Tesiph on 2007-02-26
There is no (in this case usable) recovery software for ext3 filesystems. Sorry, you have to start over.

---

### Post by bodhi.zazen on 2007-02-26
Well, that is the problem with "Boot 'n' Nuke"

The data, by design, that was over written is beyond recovery.

Perhaps you can save some data.

From the live CD, use cfdisk to make a ext3 (linux) partition in the unallocated space.

[http://www.linux.org/docs/ldp/howto/IBM7248-HOWTO/cfdisk.html](http://www.linux.org/docs/ldp/howto/IBM7248-HOWTO/cfdisk.html)

Then mount the partition and see if there is any data to recover.

---

### Post by bash on 2007-02-26
Well the data should still be there. Since Boot'n'Nuke only deleted 0.22% of my partition. Which should only be the MBR and the information that there is an ext3 partition. So I would just need some sort of a data recovery tool.

---

### Post by nereid on 2007-02-26
Maybe this could help you: [bring back deleted files with lsof](http://www.linux.com/article.pl?sid=06/10/30/1652211)

---

