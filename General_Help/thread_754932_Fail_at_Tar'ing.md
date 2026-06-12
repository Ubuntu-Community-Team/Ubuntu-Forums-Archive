---
title: "Fail at Tar'ing"
date: 2008-04-14
forum: General Help
---

### Post by Tyconic on 2008-04-14
Need some quick help here folks. 

Say I have this file, mm.c, that I have been working on pretty much non-stop over this past weekend. This morning I finally get a decent working version, I do a little dance and decide to make a copy in case DISASTER happens. 

I enter the following command:

```
tar -cvvf mm.c turtle.tar
```

Note that tutrle.tar doesn't exist (yeh its been a long weekend). I get the following ouptut:

```
tar: turtle.tar: Cannot stat: No such file or directory
tar: Error exit delayed from previous errors
```

I get a sinking feeling in the pit of my stomach. Going to check mm.c... I find that my only copy of mm.c has become binary. :lolflag: :(

I Just want to see if there is ANY way to recover my code. That is 500 lines that I did not enjoy typing the first, and I will really not enjoy going through and finding all the bugs all over again. 

Thanks in advance,

---

### Post by nick_h on 2008-04-14
I tested the command you ran and it appears that it overwrites the file mm.c with a file full of zeros.

I don't think you stand much chance of recovering the file.  I would stop using the drive immediately and search for data recovery articles on this site or google.  For example [this](http://linux.sys-con.com/read/117909.htm) link.

---

### Post by Tyconic on 2008-04-14
Well that sucks.

My wish list for 8.10: a more noob-friendly version of tar :D

---

### Post by az on 2008-04-14
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

Your data might still there as long as you don't overwrite it.

Use fls to view deleted files and icat to spit out the file (if it's still there)

[http://ubuntu-rescue-remix.org/](http://ubuntu-rescue-remix.org/)

---

### Post by nick_h on 2008-04-14
> **Tyconic said:**
> Well that sucks.

My wish list for 8.10: a more noob-friendly version of tar :D

You can use Nautilus to archive files.  Highlight the files you want to archive and then right-click on one.  Then select "Create archive" and the archive format (.tar) from the drop-down list.

Maybe useful for the future.

---

