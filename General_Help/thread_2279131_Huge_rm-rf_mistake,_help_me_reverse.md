---
title: "Huge rm-rf mistake, help me reverse"
date: 2015-05-21
forum: General Help
---

### Post by gageswenson on 2015-05-21
Hi Ubuntu community,

Tonight I made a huge, dumb mistake: I ran a rm -rf I shouldn't have. I was controlling my external harddrive via ssh, and, thinking I was in a different folder, accidentally removed many very personally valuable documents and videos.

The first thing I did was panic and install testdisk. I tried to create an image of the disk, but I canceled because I thought it was only making a backup of the non-deleted folders. The fist thing I did after that was unplug the drive. I am confident 99% of the things are recoverable. Many are common media filetypes, but I also know some plaintext that I need to look for.

I have finals tomorrow and I have to go to bed. I really cannot afford to lose the things I stupidly deleted. If anyone could give me some help taking care of this issue, I would be so appreciative. I think this will be difficult because there was a lot of data, and I will probably have to store the image of the drive on the drive. (If there a way to scan the first XXX GB of the drive?) But, I think it can be done.

Thank you for your time. If you help me get my files back. <snip> 

God bless,
Gage

---

### Post by Bucky Ball on 2015-05-21
Welcome. 

You were on the right track. Testdisk is what you're after, and you might also have luck with Photorec. Unplugging is the right thing to do. Don't use it until you are attempting to retrieve partitions or files with photorec or testdisk. 

Have a good research of these two before proceeding again so you know exactly what they do, what they are doing, and do not need to cancel half-way through. That could cause more damage and loss of files.

[Photorec]("http://www.cgsecurity.org/wiki/PhotoRec")

I always have a USB dongle with [System Rescue ]("http://www.sysresccd.org/System-tools")on it somewhere close by, it has Testdisk and Photorec along with lots of other helpful tools. Create and boot from a System Rescue disk/USB and you're covered. Good luck.

---

