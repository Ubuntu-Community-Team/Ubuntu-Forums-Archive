---
title: "Diff, kdiff3, and meld all hang when comparing directories"
date: 2021-05-17
forum: General Help
---

### Post by goemonburo on 2021-05-17
I am trying to see what the differences are between two directories.  They are large, but it seems that either they're so large that all tools for dir comparing can't handle them, or something else is going on.  Diff seems to fail after the "a"s.  Meld, being graphical, chugs through but then gets laggy and within seconds hangs altogether.  Is this normal and I should just let them run and come back tomorrow?  Or is there something else happening?

Using Lubuntu 20.04LTS, if that helps, with the apt-get versions of all these tools.

---

### Post by TheFu on 2021-05-17
Well, if you have more than about 500 files in a directory, you are asking for file system corruption and performance issues.
I've seen places with 10,000 files in a single directory, then it was corrupted.

You could do comparisons using rsync in "--dry-run" mode. That would tell you which files were different, but not what the exact differences were.

---

### Post by goemonburo on 2021-05-17
Thank you, @TheFu, I'll try that.  Certainly this has more than 500 files.  I don't think it's corrupted, since I can pull up the folder by itself and scan through its directories and files in a file manager.  But just when I'm trying to compare one directory to another the problems start.  

I'll give rsync --dry-run a try!

---

