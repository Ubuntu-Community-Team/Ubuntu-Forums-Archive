---
title: "[SOLVED] Skip routine check of drives"
date: 2008-06-19
forum: General Help
---

### Post by pb_online on 2008-06-19
I am using Kubuntu 8.04

When I boot, I get a routine check of drives and I always press ESC to skip because takes long time.

I want to disable this routine check. Can I ?

---

### Post by petzworld999 on 2008-06-19
```


sudo tune2fs -c 0 -i 0 /dev/sda1


```

where /dev/sda1 is your Ubuntu hard disk.

---

### Post by fooman on 2008-06-19
i would not recommend disabling the check.  you can however change the frequency of when it runs the check.

see this thread:

[http://ubuntuforums.org/showthread.php?t=300477](http://ubuntuforums.org/showthread.php?t=300477)

i suspect the reason it runs every time is because you are not letting it finish.  if you let the check run till its complete,  then it should not bother you again for awhile.  :)

---

### Post by pb_online on 2008-06-19
I set it up to make the routine check every 100 boots.

Thank you.

---

### Post by guraknugen on 2009-05-31
> **fooman said:**
> i would not recommend disabling the check.  you can however change the frequency of when it runs the check.

see this thread:

[http://ubuntuforums.org/showthread.php?t=300477](http://ubuntuforums.org/showthread.php?t=300477)

i suspect the reason it runs every time is because you are not letting it finish.  if you let the check run till its complete,  then it should not bother you again for awhile.  :)

I would rather prefer if the check was run when shutting down instead of when starting up. Is that possible?

Edit: Found it: AutoFsck!

---

### Post by Soul-Sing on 2009-05-31
It is possible to do it on shutdown.
===> autocheck (synaptic)

---

### Post by guraknugen on 2009-05-31
> **leoquant said:**
> It is possible to do it on shutdown.
===> autocheck (synaptic)

Just found AutoFsck. I'll try both.

Thanks.

---

