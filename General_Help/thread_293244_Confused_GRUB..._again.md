---
title: "Confused GRUB... again"
date: 2006-11-04
forum: General Help
---

### Post by Mr. Picklesworth on 2006-11-04
I finally got a spot for Ubuntu on my nice computer, in a corner of the secondary drive.

When I installed, since I was worried about removing files by accident (that thing needs to be more descriptive; partitioning is scary stuff!), I was very careful and thus ended up putting Ubuntu's partition right after a partition being used by Windows, leaving a whole other empty chunk after it.

This wouldn't do...
Unfortunately, by the time I had noticed, I had already run about 2 hours of updates (from Edgy beta to Edgy final).

Still, I decided to copy the partition to the end of my drive, leaving a nice chunk of space for Ubuntu and a single secondary drive for Windows.

(I'd best point out now that I also got the Ubuntu installer to put GRUB on my floppy disk).

Of course, the problem then arrived!
Booting GRUB (via the floppy), I am led to the GRUB prompt.
I tried some commands to get Ubuntu booting and couldn't really manage it, so that's botherly...

What I want is some sort of tool, or something (live CD, Windows, Ubuntu (via its live CD)... anything!) that will help me configure GRUB to boot from the correct place. All that has changed is the partition label (hdb4 to hdb3) and position; all the files have remained the same.

Viewing the floppy in Windows doesn't work... maybe it'll be more helpful in Linux.

---

### Post by CatKiller on 2006-11-04
I think you should be able to change the menu.lst on the floppy, although I've never used a boot floppy. Perhaps you'll find [this page]("https://help.ubuntu.com/community/GrubHowto/BootFloppy") edifying? It's relatively meaningless to me.

Bit late to mention it now, of course, but you could have used GParted to just make your partition bigger in the first instance.

---

### Post by Mr. Picklesworth on 2006-11-04
Thanks CatKiller :)

Actually, I was just about to post that I'd found and done that, and am just about to restart to see if it works...

---

### Post by CatKiller on 2006-11-05
Good luck.

---

### Post by Mr. Picklesworth on 2006-11-05
Okay, tried it.
GRUB starts up with the menu now, but it seems that with every partition I try to boot from on hdb (hd1 to GRUB), it gives me one of the following errors:
"File not found"
or "Could not mount partition"

It seems to not be recognizing 2 of my partitions, one of which is a swap partition, one of which belongs to Windows, and one of which is the one containing Ubuntu.
None of them work as is...

Trying to boot Windows (on hda, which has not changed at all) results in a "File not found" error as well.

One other spot of bother that is the reason why I can't just install it again (which at this point would have taken less time): In the Ubuntu live CD, GParted is only detecting hda. I can not change hdb with it...
(Though the installer detects hdb just fine!)

---

### Post by Mr. Picklesworth on 2006-11-05
Okay, after a few panic attacks and the unnecessary use of a CD to install Super GRUB Disk, I found my error:
The disk is hd1,1 and hdb2.

(Oooh, what a pain! Such bother, and for something so simple... I'll have to call this a learning experience).

Anyway, all is well now.

Good night!

---

### Post by CatKiller on 2006-11-05
> **Mr. Picklesworth said:**
> Anyway, all is well now.

Good night!

Glad you got it sorted. I'd had to go to bed myself.

---

