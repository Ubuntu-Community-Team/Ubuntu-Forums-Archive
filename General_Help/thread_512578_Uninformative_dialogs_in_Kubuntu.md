---
title: "Uninformative dialogs in Kubuntu"
date: 2007-07-29
forum: General Help
---

### Post by tosszyx on 2007-07-29
Hi, I've been using Kubuntu 7.04 for a couple of weeks now (my first Linux experience), and I've noticed at least two cases where I got error with totally uninformative dialogs, and after a little bit of struggle I was able to figured out what was wrong (not that it was a great deal anyway).

First case:
I was copying a 4.44 GB file to an external hard drive, but for some reason after a while I got an error that said " The process for the file protocol died unexpectedly.", and the transfer stopped. After trying several times and with diverse tools, I notice that the transfer was stopped at exactly 4GB, then I remember that my external hard disk is FAT32 formatted, so it cannot manage files bigger than 4GB.

Second case:
Trying to share a folder in Konqueror after installing samba. Right click in the folder, share, then a dialog appears where I can see which folders are shared, then click add (to put another folder for sharing), and I tries to displays a tree from root, after get stuck for a while I get ""The process for the file protocol died unexpectedly.", after several trials, a I go to System Settings and try to configure the sharing there, It all works flawlessly when  I enter to the Administration Mode.

Sorry for the lengthly post, but I hope it helps to improve other users experience and this nice OS.

Greetings

T

---

### Post by louieb on 2007-07-29
That's one of the joys of Open Source. Most of the people who write the software write it not for money but because they enjoy coding. I wrote software for 18 years I love to code and was paid well to do it. But I hated writing documentation. Error messages for the things that can be anticipated should be meaningful. But sometime you get a catchall error message like kernel panic or ttys job not ... That why things like the wiki and the Linux documentation project are needed.

---

