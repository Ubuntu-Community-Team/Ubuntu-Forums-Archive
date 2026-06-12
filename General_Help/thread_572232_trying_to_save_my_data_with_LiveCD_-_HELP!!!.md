---
title: "trying to save my data with LiveCD - HELP!!!"
date: 2007-10-10
forum: General Help
---

### Post by Elexxx on 2007-10-10
Here is the story in short (skip next paragraph if you are in hurry)

- my Vista System got the very strange error STOP:0x0000c1f5 - (if you didn't see it  - be happy - it means Win won't boot and recovery and DVD and all won't work neither) - What I found on the net the only remedy is to load a Ubuntu LiveCD and delete and re-format all windows partitions and start it all over from the DVD...

... naturally I want to save my data first - and I was really happy when I loaded the LiveCD (Ubuntu 7.04) and could see that my files are all there + that I can mount my external drive too with no problems.

Now comes the "permission to write to drive" problem I read about in other postings (but could not find a satisfactory answer there, sorry)

Do I have to get a new internal HDD (I have only one at the moment), install Ubuntu on it full scale and hope for the best?

Besides - how can I burn DVDs from LiveCD - if possible - that would be workaround too... (I can't get access to my DVD/RW though I see it in Ubuntu

Thanks in advance!

---

### Post by scrooge_74 on 2007-10-10
My take on this... you can repartition the drive to have space for Ubuntu, you can also mount an external drive and get your data out.  Also, what  I did in the past is to use Damn Small Linux which also boots from a CD, but it does not requiere the CD to stay in the CD-rom after booting, you then put a blank DVD or CD and copy your stuff out so you can wipe the drive clean.

All just install Ubuntu (keeping your data) and forget about VISTA

---

### Post by Elexxx on 2007-10-11
Thanks for answering - i tried the DSL but could not figure out how to boot with it...

Somehow i don't get the ubuntu logic aobut the persmissions - I mean I installed on an external drive and logged in and it STIlL won't let me write on my very own disk... whatever

i solved the problem by connecting the target drive for the data backup to another PC in my network and sent the 70 GB through ethernet (that took quite some time, but it seems it worked all right!)

now that my data is (more or less) safe i can get to overcoming the mentioned STOP error (however now i get i "GRUB error 21" even before the other one... incredible the PC worked just finey-fine only some days ago... :O)

have a nice one and thanks again

---

### Post by Wim Sturkenboom on 2007-10-11
Lesson:
make backups ;)

Advise:
Partition your windows drive so you have a separate partition for the data.  I think 20GB will do for Windows itself and most programs; the rest can be used for data (you can point My Documents to a directory on the second drive).
If your free dislspace on the windows partition gets below 2GB, start installing programs on the second partition (in which case it's not only for data anymore).

---

### Post by splintercellguy on 2007-10-11
Was that fine external using an NTFS partition? You needed to mount it with ntfs-3g.

---

