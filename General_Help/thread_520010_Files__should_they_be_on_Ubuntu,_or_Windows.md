---
title: "Files:  should they be on Ubuntu, or Windows?"
date: 2007-08-07
forum: General Help
---

### Post by DizzyTech on 2007-08-07
I use both Windows XP and Ubuntu dual-boot style.  Until recently, I've been using ntfs-3g in Ubuntu to access Windows and vice versa with the EXT2 File System driver ([www.fs-driver.org](www.fs-driver.org)) to share files.  It's worked swimmingly, and I even symbolically linked Documents, Music, Pictures, and Videos to their corresponding Windows folders.  However, last night Ubuntu locked up (shocking, isn't it?) and I couldn't kill X.  So, I did the natural thing and killed the power to my laptop by holding down the power button.

When I restarted my computer, Ubuntu (and its drive) was fine, but Windows wouldn't boot, nor would it mount in Ubuntu.  I managed to force the NTFS drive to mount via terminal, and copied my "important" files to my USB key.

I stuck in my Presario's recovery CD, and have been fixing Windows up all day today.  I'm about to reinstall Ubuntu (I'm too devoted to it not to), but I'm wondering of ways to avoid problems like this again.

My main theory has been to keep my documents on the [more stable] Ubuntu partition, and just use the aforementioned EXT2 driver to keep access to my files.  Would this work out better?  I want to avoid a FAT32 partition if at all possible, because it seems like the least safe method for storing my music collection and documents for use in both operating systems.

So, would it be better to place my documents and such on NTFS, keep the status quo, and use NTFS-3G as before? Or should I put them on EXT3, and use the EXT2 driver?  I'm open to suggestions.

I'm hoping to be back in Ubuntu by the end of the night!

---

### Post by merlinus on 2007-08-07
My $.05 worth -- ext3 is more stable and secure than ntfs, especially since the journaling system allows file recovery more easily and successfully.

-merlin

---

### Post by DizzyTech on 2007-08-07
I thought so, too.  I'll just let Ubuntu do its thing with importing later on this evening.

---

