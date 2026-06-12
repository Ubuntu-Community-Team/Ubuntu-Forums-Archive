---
title: "Suicidal reiserfs??"
date: 2007-07-16
forum: General Help
---

### Post by HabbitSHardin on 2007-07-16
I seem to have a strange problem when my root (/) partition is set to ReiserFS and I mount another ReiserFS volume. Couldn't find anything about it with some googling, so I'm assuming it has something to do with my computer and/or config.
This problem happens both in Ubuntu and Gentoo, the only two distros I have had installed recently, and in partition schemes such as this:
```

/dev/sda: SATA 300 GiB
       sda1: 300 GiB ntfs on /mnt/windows (irrelevant?)
/dev/sdb: SATA 120 GiB
       sdb1: 150 MiB ext2 on /boot
       sdb5: 4 GiB swap
       sdb6: 90 GiB reiserfs on /
       sdb7: 10 GiB reiserfs on /home/myname/src
```
What could happen when I mount /dev/sdb7? Oh my...
[LIST]
[*]Gentoo soft-crashed (i.e. became unusable due to constant #GPs from all apps, which I thought were related to my aggressive optimizations, but read on) with ReiserFS errors in kernel log such as "nesting into different fs". After diving a bit into the reiserfs source in kernel, I found that error should never happen (IIRC the code assumes the condition behind it has been asserted out).
[*]Ubuntu produced a similar result, not as drastic (not as many #GPs but enough to force me take the system down) but still causing some small-scale corruption in the root reiser fs, which forced me to take the ol' (tar cp | tar xp) to do a manual "conversion" of my root fs to ext3, after which all seems calm.
[/LIST]
And the million dollar question is: why can't I mount a reiser partition on another one (my root)? Am I stupid for even trying to do so? If not, am I the only one with this problem (since Google did nothing to enlighten me)? Why would it happen with two completely unrelated distros (Gentoo with a self-compiled kernel and system, Ubuntu prebuilt)?

Please, help, I'm completely puzzled. Is ReiserFS even a good choice for a root FS (seems to work OK if i don't mount another reiser partition on it). I've read the reiser docs and, while they advise not to _store reiser images_ inside a reiser partition, mounting is a completely different story... It is, isn't it?

Thank u all, ppl!:)

---

### Post by HabbitSHardin on 2007-07-17
I'm extremely sorry for my impatience, I know everyone here has better things to do and that you ppl are answering here in your free time, but I absolutely need to know at least the answer to this because there is ANOTHER computer that I need installed today:

Is it possible (by design I mean) and not risky in general, to mount a reiser (say /tmp) on a reiser /? Does that require disabling notail and/or noatime?

Thx all! :KS

---

### Post by DoktorSeven on 2007-07-17
Sadly I've had nothing but problems with ReiserFS.  It just doesn't seem that stable.

My suggestion is to use ext3, which I've found to be the most stable filesystem available.  Might not be as speedy or efficient as some other filesystems, but I'll take stability over speed any day.

---

### Post by HabbitSHardin on 2007-07-17
> **DoktorSeven said:**
> My suggestion is to use ext3, which I've found to be the most stable filesystem available.
That is definitely my choice for my desktop PC, but I'm thinking about linuxing my MCE box. It needen't be rock solid but it _must_ be lighting fast. That's the conflict.
I had thought something like this would do:
[LIST]
[*]A small (~20GiB) reiserFS on sda -> /
[*]A big (90 GiB) reiserFS on sda for P2P downloads -> /mnt/p2p
[*]Maybe a 10 GiB reiserFS on sdB -> /tmp
[*]A huge (200 GiB) XFS partition on sdB for MythTV recordings -> /mnt/videos
[*]Plus /boot, swap, etc.
[/LIST]
However, if I hit the same problem again (system crash when mounting reiser on reiser), I'll be forced to convert my root to ext3, slowing the system a tad. By the way, I'm also worried about the system startup time with 3 reiser partitions: 10 seconds for each would add half a minute in the best case! :eek:

---

### Post by rbmorse on 2007-07-17
Is ReiserFS so much faster than EXT2/3 that you would actually "feel" the difference in normal use, particularly on an A/V server?  Just curious because I've found it to be problematic as well, and just didn't seem to get enough back from it to merit living with the problems.

---

### Post by HabbitSHardin on 2007-07-17
Actually I have "felt" (subjective) reiser run faster when working with lots of small files, which usually means either source code or /tmp - especially the last one. In large files it does not give such an advantage over ext3, except when deleting - however, XFS is even faster when extremely large files (>10 GiB) and no directories are involved. This matches the profile of TV recordings, especially high quality DVB-T.
I'm currently divided over the FS to use on / (lots of small files, potential for reiser but ext3 seems more stable) and /mnt/p2p (wide range of sizes, from the 3 MiB of an mp3 to the 20 GiB of a blu-ray rip, may be either ext3 or reiser). Any suggestions on my partitioning scheme for this MCE+P2P home box? :popcorn:

---

