---
title: "Firefox sucking 10G+ RAM and all CPU"
date: 2017-08-09
forum: General Help
---

### Post by TheFu on 2017-08-09
All this week, Firefox v64.0 has been sucking 10G+ RAM and all CPU about every 10 minutes, effectively locking up the system for 45-90 seconds.  Just happened while typing in this entry.

I've been unable to find the firefox setting to limit RAM use.  Would love to limit it to 1G total.  Any ideas?

If I had 50 tabs open, I would expect this.  I have 10 tabs open.
Flash is not allowed.  Javascript is limited.

I looked at about:memory and top.
```
   PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND    
 2748 tf        20   0 8161540 1.145g  46848 R  32.6 30.7  56:58.28 firefox   

```
And Firefox's memory
```

4,261.48 MB (100.0%) -- heap-committed
&#9500;&#9472;&#9472;4,209.61 MB (98.78%) &#9472;&#9472; allocated
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;51.87 MB (01.22%) &#9472;&#9472; overhead
```

Rebooted about 30 min ago after setting up zswap.  The system only has 4G of RAM.  That did reduce the apparent lockup period greatly.

```
$ free -hm
              total        used        free      shared  buff/cache   available
Mem:           3.7G        2.2G        1.2G         65M        331M        1.2G
Swap:          4.1G        728M        3.4G

```

Disk has 23G free for /.  It is LUKS encrypted and has been working great for a few years.  The firefox issue has just gotten really bad the last week or 2.

Firefox has been bloated for years. Read last spring that Mozilla was going to fix it and all the memory leaks. Guess not.
[https://support.mozilla.org/en-US/kb/firefox-uses-too-much-memory-ram](https://support.mozilla.org/en-US/kb/firefox-uses-too-much-memory-ram) is what mozilla says.  I really like the buy more RAM suggestion. No use for a system with soldered in RAM.

---

### Post by #&amp;thj^% on 2017-08-09
> **TheFu said:**
> 
And Firefox's memory
```

4,261.48 MB (100.0%) -- heap-committed
&#9500;&#9472;&#9472;4,209.61 MB (98.78%) &#9472;&#9472; allocated
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;51.87 MB (01.22%) &#9472;&#9472; overhead
```

Rebooted about 30 min ago after setting up zswap.  The system only has 4G of RAM.  That did reduce the apparent lockup period greatly.

```
$ free -hm
              total        used        free      shared  buff/cache   available
Mem:           3.7G        2.2G        1.2G         65M        331M        1.2G
Swap:          4.1G        728M        3.4G

```


This part dose not differ too much from mine:
```
186.20 MB (100.0%) -- heap-committed
&#9500;&#9472;&#9472;171.15 MB (91.92%) &#9472;&#9472; allocated
&#9492;&#9472;&#9472;&#9472;15.05 MB (08.08%) &#9472;&#9472; overhead

```
But no problems with mine.
```
free -hm
              total        used        free      shared  buff/cache   available
Mem:            11G        1.1G        9.4G        244M        1.1G         10G
Swap:           12G          0B         12G

```
But the only way I know of to minimize memory for firefox v54 is in that same tab "about:memory"
At the top mine shows in screenshot provided.
There was a few options for it also...but no manual specific way to set permanently that I could see.
Kind of a flush cache is how I took it.
Kind Regards

---

### Post by TheFu on 2017-08-09
Flushing didn't help much - maybe 500MB.

I'm thinking of running it inside a dedicated container limited to 2G of RAM.  The lockups have definitely been helped by zswap, but still happens about every 5 min for 30 sec at a time.  Can't alt-tab to other active processes.

An alarm was going off last time it locked up.  Even the audio stopped.

```
$ uname -a
Linux cc3550 4.10.0-30-generic #34~16.04.1-Ubuntu SMP Wed Aug 2 02:13:56 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
```

BTW, this kernel update helped solve video lockups that required the BRS solution, so that is definitely better.

Comparing a 12G RAM system with a 4G RAM system might not be helpful.  Things SHOULD be handled very different.

---

