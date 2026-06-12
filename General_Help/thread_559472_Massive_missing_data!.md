---
title: "Massive missing data!"
date: 2007-09-25
forum: General Help
---

### Post by Chibi on 2007-09-25
I appear to have come across a serious problem, more serious than any problem I have ever encountered in my life. The entirety of my digital personal data has somehow vanished; or maybe I should say access to it has.

 You see, I have this mobile hard drive that I use in Linux and Windows, I run a fsck on it whenever I have the time. 500 Gigabytes of data, and essentially where my entire existence is backed up, from birth certificates to reports, financial documents, music, movies, etc. I can access the disk and most of the information fine, however, mysteriously, several folders have become files, and the files are no access.

 I've tried what I could aside from things I am paranoid would damage it, but I can not seem to do anything about it. My fsck reports a strange chain of errors that I am paranoid of choosing:
HTREE directory inode 20955188 has an invalid root node.
Clear HTree index<y>? no

HTREE directory inode 20955188 has an unsupported hash version (232)
Clear HTree index<y>? no

HTREE directory inode 20955188 uses an incompatible htree root node flag.
Clear HTree index<y>? no

HTREE directory inode 20955188 has a tree depth (9) which is too big
Clear HTree index<y>? 


The only other peice of information I can give is that I have been running it in ext2 mode on windows, while it is an ext3 filesystem

---

### Post by anaconda on 2007-09-25
I have also encountered a directory, which stopped working. Couldn't access it with nautilus(it said it was a file), but good old terminal accessed it without problems.. So that I was able to copy them somewhere else..

can't really understand why. because I used to assume that Nautilus would use the same commands eg. cd, cp, mv etc.. and just work as a graphical interface, but no. I have also encountered that nautilus refused to copy a file and terminal just copied it!

It is a long shot, but hope this helps.

---

### Post by rbmorse on 2007-09-25
You've got your entire life on one physical drive with no backups?

Might want to rethink that strategy.

---

