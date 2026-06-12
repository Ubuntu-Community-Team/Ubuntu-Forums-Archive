---
title: "first time file access makes applications unresponsive"
date: 2013-03-19
forum: General Help
---

### Post by wormhole on 2013-03-19
Hi! Sorry if duplicate issue, coulnd't find anything myself.

A very annoying problem started a few weeks ago: after login, opening directories (file listing), invoking rename on files, or launching certain applications (e.g. Pidgin - probably loading logs) causes the system to become very busy (especially the hard drive) for a few seconds, during which that directory or application is unresponsive (sometimes the entire system). I can move the mouse cursor and type, but not in that application/directory, and it's very jerky anyway. Subsequent repeats of those commands/accesses have no issue. This happens both on my ext3 root filesystem and my shared NTFS partition.

For about a week, I kept the root filesystem with only about 100 MiB of free space, with a few minor program updates (limited number of file writes). Though I would be very surprised if this is a fragmentation issue. And the NTFS partition behaves the same after defragmentation.

The issue persisted after the routine fsck during booting. Stats returned for the root filesystem: 323022/1233024 files (8.3% non-contiguous), 2181172/2464552 blocks
I also tried setting swapiness = 10 as a quick fix, but no effect.
I suspect the ntfs-3g driver, but then again I also have problems on ext3.
I upgraded the kernel a few times so I don't remember after which version this started, but I've been using the 3.5.0 versions for a longer time than this problem. I'm very busy with work so I didn't have time to play with older kernel versions.

I have Kubuntu 12.04(.02). I don't think KDE's the issue here, and I've switched off indexing/metadata services from the beginning (don't need them). I put the prefix just in case.
I'm running kernel 3.5.0-26.42-generic, 64 bit.

I don't know if my hardware specs are relevant here. SMART shows no failures.

Any clues?

---

