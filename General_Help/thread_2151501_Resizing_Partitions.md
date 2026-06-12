---
title: "Resizing Partitions"
date: 2013-06-04
forum: General Help
---

### Post by justinwbb on 2013-06-04
My computer has run out of memory, which is a pretty big problem.  I'm trying to see what I can do with my limited linux knowledge, but I found out the partition that's out of memory is /dev/sda7. /dev/sda5 is almost completely empty, so I want to shrink /dev/sda7 and use the unallocated space for /dev/sda5. The problem is that I can't get any cd/dvd burning programs to work, so I can't make a linux live cd.  So I need to either resize two partitions in GParted while linux is running, or figure out how to make a linux live cd on a cd when i can't burn it.

---

### Post by Cheesemill on 2013-06-04
Do you have a USB drive? You can use that to boot from.

Can you post a screenshot of gparted please so we can see exactly how your partitions are set up.

Also I assume you are talking about hard drive space not memory, they are completely different things.

---

### Post by grahammechanical on 2013-06-04
Be careful and think about what you have just written.

> [COLOR=#000000]I found out the partition that's out of memory is /dev/sda7.[/COLOR]

> [COLOR=#000000] I want to shrink /dev/sda7[/COLOR]

If you shrink sda7 you will most certainly lose the data that is filling up the partition. It is better to remove/delete unnecessary files on /devsda7 or copy them over to /dev/sda5. What partition is Ubuntu installed on? If it is installed on sda7 then you will not be able to re-size sda7 whilst running Ubuntu. This is why it is recommended that we do this from a live session.

If Ubuntu is installed on sda7, then it would be possible to resize sda5 from Ubuntu on sda7 but you would need to install Gparted. It is on the Ubuntu live session but not installed in Ubuntu on the hard disk and for a good reason.

Perhaps you could move many of your data files onto sda5. I have a partition set aside especially for all my data. In this way if I need to re-install, as I did yesterday, then my important documents and other files are not at risk.

Regards.

---

### Post by Charlotte18 on 2013-06-04
Before you start moving data and resizing, I recommend that you use clonezilla or some other backup software to back up the drive or at least the partitions in question to an external usb drive.

I also agree with the last poster that you won't be able to accomplish what you want to do unless you can boot from cd or usb thumb drive.

---

### Post by Mark Phelps on 2013-06-05
It's very hard for us to provide detailed advice without first seeing the layout of partitions on your drive (what you are calling "memory").  You can't exchange space between partitions unless they are right next to each other, and based on what you've said, that might  not be the case.

You need to open a terminal and enter "sudo fdisk -l" (that's a lowercase L, not a one).  That will list out the partitions on your drive.

Also, you can NOT make change to partitions that you are using, so sorry, if either sda5 or sda7 is in use, you will have to boot from a USB or CD to make the chantges.

---

