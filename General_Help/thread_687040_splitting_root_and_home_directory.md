---
title: "splitting root and home directory"
date: 2008-02-03
forum: General Help
---

### Post by afderrick on 2008-02-03
So I want to reformat my hard drive to seperate my root and home partition.  I tried to do this when I first installed but didn't do enough homework to really know how to do it.  Now that I think I understand better I want to do this.  I have found some instructions at: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) which hopefully is a good source.  My only concern is have you done this and will I have any problems with my application menu not referencing the correct file anymore or will everything port over if proper?

As a side note, I will be backing up all my information on an external hard drive.

---

### Post by pjkoczan on 2008-02-03
> **afderrick said:**
> So I want to reformat my hard drive to seperate my root and home partition.  I tried to do this when I first installed but didn't do enough homework to really know how to do it.  Now that I think I understand better I want to do this.  I have found some instructions at: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) which hopefully is a good source.  My only concern is have you done this and will I have any problems with my application menu not referencing the correct file anymore or will everything port over if proper?

You don't have to be concerned about that. This isn't like Windows where the general practice is to have drive letters for each partition/disk. Linux (and Unix, too) use mount points, which put a filesystem at a specific directory. The user and most programs just see it as another directory. It doesn't matter to them whether it's a disk or a normal folder, all programs would see is /home/[user]/files and magically it all works. Your concerns are understandable but unfounded.

Be careful when reinstalling or upgrading your OS, so that you don't accidentally overwrite your /home partition. You might also have to manually re-mount /home and re-edit /etc/fstab after a fresh install.

> As a side note, I will be backing up all my information on an external hard drive.

Well done.

---

### Post by afderrick on 2008-02-04
Actually I want to split the root and home so I can easily upgrade and change my OS without problem.  Mostly just to upgrade to the new ubuntu coming out in April.

---

### Post by zvacet on 2008-02-04
Just follow instructions you found and you will have things in the way you want it to be.

---

### Post by pjkoczan on 2008-02-04
That should work to accomplish your goal of easily upgrading. I just don't have experience doing in-place  upgrades myself (I like to start completely fresh) and I originally started my Linux career on Red-Hat-based OS's, where the installer likes to completely overwrite any disk it finds. Ubuntu, thankfully, doesn't do that.

Be sure to test and have backups at the ready (good practices in general).

Sorry for any confusion.

---

