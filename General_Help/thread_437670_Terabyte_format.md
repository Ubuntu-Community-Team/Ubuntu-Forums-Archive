---
title: "Terabyte format"
date: 2007-05-09
forum: General Help
---

### Post by Lowfront on 2007-05-09
Just wondering what your thoughts for my Terabyte external I'm getting tomorrow.

I'm using it for straight up media mostly movies, tv, music.

I'd like to be able to easy go from windows to ubuntu with it.

Ext 3?

Maybe 250gb partitions or what?

---

### Post by spin2cool on 2007-05-09
If you're only using it on one or very few windows computer, ext3 would be fine.  You can install [Ext2 IFS](http://www.fs-driver.org/) on the windows drives and access them no problem. 

I also hear that Linux NTFS support has gotten much better, so that's also an option.

The most portable and safe option would be FAT32, but then you can't have files larger than 4GB.  This may or may not be a problem for you.

---

### Post by Lowfront on 2007-05-09
How is FAT32 the most portable and safe???

4 gig being the max will prob be a problem.

---

### Post by Lowfront on 2007-05-09
double post

---

### Post by spin2cool on 2007-05-09
> **Lowfront said:**
> How is FAT32 the most portable and safe???

- Windows XP has no native support for Ext2/3.  Ext2IFS is solid, but not perfect - back when I dual booted, I very occasionally had crashes caused by it.  It also comes with no guarantee that it will always work properly.

- Linux has no native support for NTFS.  The NTFS drivers out there are getting better, but most come with a caveat - the developers say they can't guarantee that you won't lose data or hose your filesystem.  

-Fat32 is natively supported by both OSes and you should never have any kind of compatibility issues.


As for the 4GB file size issue?  Stop pirating DVDs, and it won't be an issue :-P  (yes, I know - lots of legit uses, yadda yadda :-))

---

### Post by mckryptyk on 2007-05-09
You must be joking right? :confused: 

Linux does have stable ntfs write support. It is called "ntfs-3g".
It works, it is stable and I have seen no performance issues with it at all . 

I have put it through all kinds of punishment such as writing lots of data to it  (<200 GBs at a time) and deleting from it (same as writing) because I use it for a database backup for work when I need to copy certain appliance based databases.

The developers of it have done much more "stress-testing" on it than that as well.

If you want to try it go here for more info:

[ HOWTO: NTFS with read/write support using ntfs-3g (easy method) ]("http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g+easy")

It uses FUSE (Filesystem In USErspace).

Also because it is written to act in userspace, it makes writing new filesystem drivers for it much easier than kernel based drivers meaning, linux will see a lot more partition and file support in the coming years.

Cheers.

---

### Post by spin2cool on 2007-05-09
Thanks for proving me wrong.  The last time I attempted NTFS support was two years ago, and it was buggy as all hell.  Glad to hear that things have improved since then.

---

### Post by Lowfront on 2007-05-09
What about the NTFS support thats included with fiesty is that what your talking about?

Also would it be dumb for me to just make it one big partition?

---

### Post by mckryptyk on 2007-05-09
spin2cool: You are right that two years ago it was buggy, dangerous and unstable, but that was not ntfs-3g. (I only write this to make the clear distinction for those just reading this now :))

To use ntfs-3g you will have to enable the 'multiverse' repositories (if I remember correctly) and 'sudo apt-get install ntfs-3g ntfs-config' or use synaptic to install them. Then you must run ntfs-config.

If you follow the previous link in my last post, you will find all the information that you need.

Lowfront: I'm not too sure if you want to use one giant partition or not but, I found no problems exactly doing that.

Be sure to unmount cleanly each time you are done with it, (ubuntu will do this for you usually) 
if not you could use windows to mount/unmount cleanly to repair any problems.

Cheers.

---

### Post by Lowfront on 2007-05-09
So the NTFS sopport with fiesty is not this stable program you are talking about?

---

### Post by mckryptyk on 2007-05-10
You need to go here:

[Ntfg-3g]("http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g+easy")


This will help you.
If you want more info go to [Ntfs-3g Homepage]("http://ntfs-3g.org/")
and here:
[Ntfs-3g official install method]("http://ubuntuforums.org/showthread.php?t=217009")

I can't officially say that it will be included in the next ubuntu release (I don't work for Canonical)
but I would not be surprised if it was.

If you are using feisty just skip the adding repositories part of the how to and enable multiverse and universe repositories instead.

You can continue the howto from then on.

Cheers.

---

