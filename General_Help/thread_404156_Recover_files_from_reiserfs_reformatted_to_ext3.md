---
title: "Recover files from reiserfs reformatted to ext3"
date: 2007-04-08
forum: General Help
---

### Post by aashay on 2007-04-08
Is there any way to recover files from a SUSE installation on a reiserfs which was accidentally overwritten by a Ubuntu install (now ext3) Both the partitions, possibly, are not the same size. The partition was deleted using gparted in the Ubuntu setup.  Products which i have found so far: Nucleus data recovery and photorec

---

### Post by kidders on 2007-04-09
Hi there,

I'm not a forensic data recovery guru, so please read this post with that in mind! It's possible that there may be a smarter way to solve your problem, but here's what I would try, if this happened to me...
[LIST=1]
[*]Immediately stop using the Ext3 filesystem, so it doesn't extend any further into the underlying ReiserFS filesystem ... assuming the Ext3 one is smaller, of course.
[*]Try to establish the physical on-disk location where the (hopefully contiguous) Ext3 data blocks end, and the lost ReiserFS files begin. (You'll need a calculator!)
[*]Dump everthing from that point to the end of the original ReiserFS partition into a file.[/LIST]Now, you'd be able to make copies of that file, and try as many data recovery strategies as you can find, without fear of worsening your situation, or confusing data recovery programs with lots of data structures belonging to two different filesystems.

The first thing I would try would be a metastructure-based recovery. There are a few apps around that are capable of doing this. The idea is that certain files (some images, multimedia files, tarballs & other archives, and so on) have a pretty rigid internal structure that simply doesn't vary. It is possible (in fact it's quite easy) to use this fact to perform a completely non-destructive recovery attempt, to help give you an idea of how much data still exists, and what kind of condition it's in.

With some luck, promising results will encourage you to persevere with more complicated, time-consuming options. On the other hand, you might discover that there is simply nothing of use left to recover.

I hope that's of some help.

---

