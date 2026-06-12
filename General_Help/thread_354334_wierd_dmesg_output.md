---
title: "wierd dmesg output"
date: 2007-02-05
forum: General Help
---

### Post by chronusdark on 2007-02-05
What does this mean...only thing new is i upgraded my ram to 2GB
```


[17181086.836000] NVRM: Xid (0001:00): 32,  L10 -> L1 temp 104C
[17181196.836000] NVRM: Xid (0001:00): 32,  L10 -> L1 temp 104C
[17181647.832000] NVRM: Xid (0001:00): 32,  L10 -> L1 temp 104C
[17181903.828000] NVRM: Xid (0001:00): 32,  L10 -> L1 temp 104C
[17182330.824000] NVRM: Xid (0001:00): 32,  L10 -> L1 temp 104C
[17187831.744000] NVRM: Xid (0001:00): 32,  L10 -> L1 temp 104C
```
got those during a game

and these
```

[17192217.768000] NVRM: Xid (0001:00): 6, PE0000 1fdc 00000002 0000f248 00ffffff 03200000
[17192217.784000] NVRM: Xid (0001:00): 30,  L0 -> L0

```

after normal use

i have never seen these before can someone help me solve this mystery??

---

### Post by Stephen Howard on 2007-02-06
Hmm, looks like nvidia card errors.  I don't know what error 32 means, but presumably its temperature related.  If no one here can help its probably best to go to the [nvidia on linux forum ]("http://www.nvnews.net/vbulletin/forumdisplay.php?f=14") and ask there.

Also, run memtest86 (on the boot menu) just to see if there's some bad ram.

---

### Post by gradedcheese on 2007-02-06
this will sound weird, but somewhere I've heard of problems with Nvidia cards and PCs with more than some amount of RAM (maybe 2GB?).  It has to do with their drivers and possibly hardware issues.  It might be interesting to take some of the RAM out and see if the problem goes way :)

---

### Post by chronusdark on 2007-02-06
the wierd thing is im not having any problems...the computer is running fine

i will check the nvidia forums, but if anyone knows what this is please tell me

---

