---
title: "[SOLVED] cannot mount volume - of jfs partitions from my laptop hard drive"
date: 2008-04-11
forum: General Help
---

### Post by bluepowder7 on 2008-04-11
yesterday my laptop went POOF while i was using it.  i've taken the hard drive out so that i can recover my files and settings and whatnot, but i'm having trouble mounting it.  it's a SATA drive, and on it my / (root) and /home partitions are JFS type.  i have it plugged into my desktop (as basically another internal SATA drive).

when i crack open nautilus, i can see all the partitions that are on the laptop's hard drive - at least as a crude list of "1004.3MB volume" and "1004.3MB volume (2)" and so on.  when i attempt to either mount it or browse its contents, i get a pop-up error message:

[IMG]http://i106.photobucket.com/albums/m244/GregR7/Screenshot-gnome-mount.jpg[/IMG]

do i need to run a file system check on those various JFS partitions?  do i need to sudo my way through some of this?  i think that once i can get those partitions mounted (even if just one at a time), i can recover my settings and make progress...

---

### Post by bluepowder7 on 2008-04-11
ok, turns out i needed to do a fsck on all the partitions, and it mounted properly after that.  hmm, nice thing about all the JFS partitions is that they checked VERY quickly and had zero problems.  my ext2 and ext3 partitions took a bit of time, and two of them had a few issues that got fixed.

---

