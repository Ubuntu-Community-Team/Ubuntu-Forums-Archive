---
title: "&quot;Cannot find GRLDR&quot;"
date: 2007-09-28
forum: General Help
---

### Post by Sp3ctre18 on 2007-09-28
Hi everyone. Been hearing about linux for years of course, but never got into getting because of all that messy partitioning stuff and expenses, and as much as a geek i may be, not enough for that kind of stuff; guess you could say i'm a geek with working and using software, not really with technical and codings and commands and stuffs. Anyway, then I found wubi, and i've installed with no problem, and Ubuntu shows up at the boot screen.

Problem is, ubuntu won't run, I get that evil cannot find GRLDR thingy.

I'm running windows XP home, drive partitioned into C and D drives, both regular, usable partitions, file system s NTFS.

I've already searched online, but can't find any use; all the "help" and replies (even on this board) seem to assume the guy knows what to do with what to me seem like random words (possibly code that goes who knows where) and some GRUB thing that doesn't even seem to tell clearly how to install or run.

hope someone can tell me how to fix this, thanks! :)

PS: yes, "GRLDR" and "menu.lst" are in C:\

---

### Post by bean123 on 2007-09-29
Please make sure that you are using the latest version of wubi, old version may has bugs that cause this problem.

Another note is that grub4dos does not support dynamic partition.

---

