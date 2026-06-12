---
title: "questions"
date: 2008-03-12
forum: General Help
---

### Post by kingbob38 on 2008-03-12
I just installed ubuntu and have couple questions about the filesystem

1. Does it fragment (ext3)

2. Is it journalled like ntfs.

3. Is ext3 the same as the other filesystems? (jfs,fat, hfs+

---

### Post by amingv on 2008-03-12
1. No, at least not as significantly as other filesystems.
2. Yes, ext2 isn't though.
3. In what sense do you ask this? I mean, they're all filesystems, but quite different in their operational procedures. (If they all were the same, there'd be no point in having so many.)

---

### Post by locosmurf on 2008-03-12
amingv pretty much summed it up. I would like to mention that if you mean your third question in a sense of are they compatable with one another, then in my experience no (someone back me up on this). And, like amingv mentioned, they are all very different in they way they operate.

---

### Post by articpenguin on 2008-03-12
ext3 has problems with lookups in directorys (1000+ files) 

I find no difference bewteen the filesystems except that JFS and XFS dont have fixed inodes and are better with large files.


I use JFS because i have a lot of vbox images. Also Reiserfs xfs and jfs dont have the problem with directorys as they use B+ trees.

---

