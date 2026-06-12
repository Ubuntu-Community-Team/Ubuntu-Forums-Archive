---
title: "Memtest Runs Periodically"
date: 2016-08-21
forum: General Help
---

### Post by box02-0 on 2016-08-21
Ubuntu 14.04

Hi.

My system has recently begun running some sort of memory test after every so many boots.The process takes about 30 seconds, and is quite annoying. I would prefer to invoke such a test on demand, rather than have the system decide when to run it. I'm not sure how, or why, this feature started.

How can I remove the automatic running of this test?

Thanks,

M..

---

### Post by ajgreeny on 2016-08-21
> **box02-0 said:**
> [I]Ubuntu 14.04

Hi.

My system has recently begun running some sort of memory test after every so many boots.The process takes about 30 seconds, and is quite annoying. I would prefer to invoke such a test on demand, rather than have the system decide when to run it. I'm not sure how, or why, this feature started.

How can I remove the automatic running of this test?

Thanks,

M..
[/I]
There is no way we can help you without knowing what that "memory test" really is; it might be a filesystem check (look for the word **fsck**) which normally runs at a predetermined interval of *numbers of boots* or *time interval*.

Tell us more detail about what you see when this happens and perhaps we may have an answer for you.

---

### Post by banceu_sergiu_ione on 2016-08-21
>  You should strongly consider the consequences of disabling mount-count-dependent checking entirely.  Bad disk drives, cables, memory, and kernel bugs could all corrupt a filesystem  without marking the filesystem dirty or in error.  If you are using journaling on your filesystem, your filesystem will never be marked dirty, so it will not normally be checked.  A filesystem error detected by the kernel will still force an fsck on the next reboot, but it may already be too late to prevent dreplace /dev/sdj* with your disck path filesystemata loss at  that point.  " quote from man tune2fs " 

This is how you check how your system is set for next check

-replace /dev/sdj* with your disck path filesystem

```
 sudo tune2fs -l /dev/sdj* | egrep -i 'mount count|check' 
```

---

