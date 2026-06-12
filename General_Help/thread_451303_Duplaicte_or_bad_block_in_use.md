---
title: "Duplaicte or bad block in use"
date: 2007-05-22
forum: General Help
---

### Post by GabrielWolff on 2007-05-22
When trying to boot I get a message that my file system contains errors, and after a while of the forced chek, I'll get the following message:
```
Duplicate or bad block in use!
```
later on I get a huge list of ```
Multiply-claimed block(s) in inode xxxxxxx: xxxxxxx
```
and then three times: ```
[xxxxxxxx.xxxxxx] hda: drive not ready for command
```

What's wrong?
How do I get it fixed (or at least a chance of getting important files before I reinstall the OS...)?

Gabriel

---

### Post by mercuccio on 2007-10-03
Hi there. I have the same problem here. I saw the following thread in this forum:
[http://ubuntuforums.org/showthread.php?t=522059]("http://ubuntuforums.org/showthread.php?t=522059")

Quoting:
[INDENT]Find out it your hard drive is good, first. Download the hard drive diagnostic program from the manufacturer of the hard drive. If it tests good, then you can do the fsck stuff. But if not, theres really no point other than to salvage data. The hard drive would then heed to be replaced, and Ubuntu reinstalled.[/INDENT]

[INDENT]
fsck -v (this switch means be verbose) it will start a check again but this time after a short while it will ask you if you want to re-write each block, just answer yes.[/INDENT]

I will try it now and give a feedback later.

Good luck to both of us!

Mercuccio

---

### Post by mercuccio on 2007-10-03
Hi again,

I tried the quoted help and it worked fine. You must be aware that some data loss might occur, if the bad block haven't cause the data loss themselves. 

Good luck.

Mercuccio

---

