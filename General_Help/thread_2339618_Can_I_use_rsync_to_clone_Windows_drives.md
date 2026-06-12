---
title: "Can I use rsync to clone Windows drives?"
date: 2016-10-10
forum: General Help
---

### Post by Cursed Lemon on 2016-10-10
So, part of my current backup procedure here at home involves drive mirroring. Unfortunately, my new motherboard doesn't have hardware RAID (and my old one was buggy as all ****), so I'm relegated to using Macrium Reflect's drive cloning feature to create an exact copy of a hard drive so that in the event of a hard drive death, I can just switch over to the other hard drive with no downtime. 

Unfortunately, Macrium Reflect does not do incremental backups (or at least the free version doesn't), so it's a little taxing to do a full 1TB worth of data backup every single time, both on my patience and on the drive hardware. One possible solution that I could live with is to load up Linux on a thumb drive and do incremental rsync'ing between drives. However, I need to know whether or not rsync can create an *exact *drive clone - no extraneous files, no weirdly misplaced folders, no strange conflict over NTFS, nothing like that. 

Right now, Reflect creates PERFECT backups. Can rsync do the same, using the procedure I described?

---

### Post by papibe on 2016-10-10
Hi Cursed Lemon.

Unfortunately no. 'rsync' is for files, and folders, not for disk imaging.

On the other hand, you have other options: clonezila, dd, ddrescue, Mondo Rescue, Partimage, Acronis, etc.

However, AFAIK, none of them support incremental or differential images.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by Cursed Lemon on 2016-10-11
Hngggnhghgnhghgh well, maybe I'll drop the money on Macrium then, it really is a fantastic program. 

Thanks anyway!

---

### Post by Bucky Ball on 2016-10-11
I see no version for Linux on the Macrium website, though, so guessing you'll be doing this backup from Windows ... :-k

---

### Post by Cursed Lemon on 2016-10-11
> **Bucky Ball said:**
> I see no version for Linux on the Macrium website, though, so guessing you'll be doing this backup from Windows ... :-k

I was only venturing a guess with rsync because I'm handy with Linux and the free version of Macrium doesn't allow for incremental backups, and I don't know of any other (free) Windows software that does them either. 

Incidentally, if one wanted to do incremental disk cloning on Linux (specifically, performing it on an online disk), anyone know what the best software would be?

---

### Post by sudodus on 2016-10-11
You can use ***Clonezilla*** to clone drives with linux and Windows (also dual boot and multiboot drives). It is free (FOSS). You can download an iso file, and read the description at [http://clonezilla.org](http://clonezilla.org)

*Edit:* If you want incremental backups, there are many linux tools for example ***rdiff***. You should do that separately from the cloning task.

[http://rdiff-backup.nongnu.org/](http://rdiff-backup.nongnu.org/)

---

