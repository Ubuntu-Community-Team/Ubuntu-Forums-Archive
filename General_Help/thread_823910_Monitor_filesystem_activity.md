---
title: "Monitor filesystem activity?"
date: 2008-06-09
forum: General Help
---

### Post by houdodu on 2008-06-09
Are there any linux apps to monitor live filesystem access?

To see each write, close, open, etc. as they happen.

I had one on windows that was very helpful, but I can't seem to figure out an analogue for Linux.

---

### Post by bingoUV on 2008-06-09
To monitor a specific program's activity, use strace. Either start the program with strace
```

strace <program name> <options>

```

Or, attach strace to an already running process
```

strace -p <pid of the running process>

```


If you want to monitor all program's activity, do as in [http://ubuntuforums.org/showpost.php?p=4834642&postcount=3](http://ubuntuforums.org/showpost.php?p=4834642&postcount=3).

If you just want to monitor the amount of filesystem activity processes are doing, install iotop.

---

### Post by houdodu on 2008-06-09
wow, theres no cleaner way to monitor all the activity? i'm surprised.

---

### Post by r0g on 2008-09-11
Whoops, actually ignore comment below, I hadn't read yer man's comment correctly and hadn't realised he's talking about blockdump!...

Roger

<stupidity>
Cleaner?!
Cleaner how???

I love that's built in and you don't have to schlep over to sysinternals to get a gui app to do it! It's got all the same info and a f***bunch more options I really don't see why you're complaining :-/
</stupidity>

---

### Post by encore2097 on 2010-01-06
> **houdodu said:**
> Are there any linux apps to monitor live filesystem access?

To see each write, close, open, etc. as they happen.

I had one on windows that was very helpful, but I can't seem to figure out an analogue for Linux.

In case someone else needs it

iwatch - realtime filesystem monitoring program using inotify

---

