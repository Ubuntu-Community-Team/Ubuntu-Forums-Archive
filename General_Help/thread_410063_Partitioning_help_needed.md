---
title: "Partitioning help needed"
date: 2007-04-15
forum: General Help
---

### Post by drbob07 on 2007-04-15
I need help in repartitioning my hard-drive.

First off, a screen-shot so you can see what I'm talking about
[IMG]http://img104.mytextgraphics.com/photolava/2007/04/15/parted-1i1yjjp0.png[/IMG]

I want to resize the Linux Partition (to the right of unallocated space), so that it takes up all of the unallocated space, but I can't for the life of me figure out how to do it!

It seems to me like an operation similar to what the installer does, cut a chunk out of NTFS, leaving me with a lot of unallocated space, but now I want to put that unallocated space into the Linux (EXT3) partition.


So how do I go about doing this :confused:

---

### Post by viciouslime on 2007-04-15
The reason you can't work out how to do it, i'm afraid, is because you can't.

You can resize the one to the left of the free space into it, but not the one to the right. Annoying that...

Partition magic is capable of doing this, however, be very wary, I have heard many a story about partition magic killing linux partitions. That said, it has always worked fine for me, it is ntfs partitions it has always had troubles with for me. I've had partition magic wipe out many an ntfs partition...

If you have another hard drive, locally or in another computer, I would back everything up to that, just in case.

---

### Post by indytim on 2007-04-15
if you're accessing GParted from your booted operating system, you will probably not be able to re-size the partition as it is the active partition and you cannot unmount your current operating system.


If you're using GParted Live:

> click on the ext3 partitition
> from the menu (top, select resize partition)
> drag the ext3 partition to the left into the unallocated space
> click the apply button.

The graphic layout should now show the reconfigured partitions.

> Re-boot


If you don't have a copy of GParted Live, here's the link for it:

[GParted]("http://gparted.sourceforge.net/index.php")

Hope this helps.

IndyTim

---

### Post by Doug11 on 2007-04-15
Indytim is right. The only way to resize it would be to use the live GParted cd. The reason being is you have to unmount it before you can resize it. (If I am wrong , someone please correct me.) But this should fix your problem.

---

### Post by drbob07 on 2007-04-15
Yeah I know that you need the LiveCD. I was just in my OS for screenshot purposes.

I'll try using Partition Magic I suppose. Otherwise I could always just wait and buy a 160gb so linux can have its own hard drive :)

---

