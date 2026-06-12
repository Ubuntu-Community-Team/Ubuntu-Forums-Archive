---
title: "New Hard drive, what FS?"
date: 2007-11-28
forum: General Help
---

### Post by skymera on 2007-11-28
im getting a new hard drive soon, a sweet 500GB, mainly for windows games but im gonig to reinstall ubuntu on it.

which filesystem shouldi  use?

im currently on EXT3, but which filesystem has faster speeds?

ive heard of Reiser, whats that like?

also when is EXT4 released?

---

### Post by disturbedite on 2007-11-28
just use ext3 for ubuntu.

---

### Post by lespaul_rentals on 2007-11-28
Are you going to run Windows on it?  If so, go FAT32.

ext3 is the all-around most universal file system.  Every Linux distro supports it, ext2 tools will work on it, it's journalled, which is great, and it's fairly reliable and fast.

reiserfs is a great filesystem.  I've heard mixed reviews, some of which are "Switch, it's better," while others say "It's great, but not much different than ext3."  Up to you, really.  If you program, compile, and such, you will notice a difference.

JFS is the best all-around, from what I've heard from muliple sources.  It handles small, medium, and large files well, it's quite fast, and it's journalled.  I honestly have never tried it, but it seems to be quite good for many uses, and a favorite for many people.

XFS is good for large files, such as .iso files, DVD rips, the like.

ext4 is already out, but it's still in development.  I think the stable version comes out sometime next year.

---

### Post by skymera on 2007-11-28
JFS sounds good :)

i'll read up more on it.

---

### Post by isecore on 2007-11-28
If you're not sure which filesystem you need - stick with ext-3.

Reiser, JFS, etc are all very capable filesystems, but unless you really know you're going to need them there's no need to scratch your head over it. Ext-3 will do just fine. If you know you're going to need Reiser, then you're already knowledgeable enough to make such a decision.

Ext-3 is essentially Ext-2 with journalling tacked onto it. So far I haven't heard the slightest whisper of anything named "Ext-4" and I personally don't see why since the only thing lacking from an otherwise decent allround filesystem such as Ext-2, and that was fixed with Ext-3.

---

### Post by jfinkels on 2007-11-28
ext3

---

### Post by atlfalcons866 on 2007-12-02
JFS is very good. But IBM has decided not to support jfs anymore. But it is still maintained by 1 or 3 people.

---

### Post by skymera on 2007-12-03
i was thinking of the Reiser FS.

but hearing the guy is in trial for murder, im thinking again :)

may just stick to EXT3, seems most common

---

### Post by mahousaru on 2007-12-03
> **skymera said:**
> i was thinking of the Reiser FS.

but hearing the guy is in trial for murder, im thinking again :)


Especially if you factor in that v3 is no longer developed and v4 is still missing some functionality...

---

### Post by LaRoza on 2007-12-03
If you are going to be using this drive with Windows, I suggest NTFS, otherwise ext3.

---

### Post by Sef on 2007-12-03
> i was thinking of the Reiser FS.

but hearing the guy is in trial for murder, im thinking again 

That is true.   However, he sold his company, so he no longer owns it.    I used Reiserfs, and it is good.   I find it and ext3 very similar, but reiserfs never needs defragging.

---

### Post by atlfalcons866 on 2007-12-03
> **Sef said:**
> That is true.   However, he sold his company, so he no longer owns it.    I used Reiserfs, and it is good.   I find it and ext3 very similar, but reiserfs never needs defragging.

are you saying ext3 needs defragging? i have a 4.3Gb ubuntu DVD iso that is in 20000+ extents. I am using ext3.

---

### Post by skymera on 2007-12-04
> **Sef said:**
> That is true.   However, he sold his company, so he no longer owns it.    I used Reiserfs, and it is good.   I find it and ext3 very similar, but reiserfs never needs defragging.

looks like its between ReiserFS and EXT3.

ima go Google and find comparisons :)

---

### Post by Me! on 2008-02-12
You can see:
[http://en.wikipedia.org/wiki/Comparison_of_file_systems](http://en.wikipedia.org/wiki/Comparison_of_file_systems)
[http://en.wikipedia.org/wiki/Ext3](http://en.wikipedia.org/wiki/Ext3)
[http://en.wikipedia.org/wiki/ReiserFS](http://en.wikipedia.org/wiki/ReiserFS)

Notice that you can not undelete your files in ext3 !

I don't know about reiserFS

---

### Post by articpenguin on 2008-02-12
Reiserfs is unmaintained and it dosent take hard poweroffs as good as ext3 or JFS.

---

