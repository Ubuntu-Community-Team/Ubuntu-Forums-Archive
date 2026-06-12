---
title: "Turned On My Monitor To See What Looked Like a Kernel Dump"
date: 2013-02-09
forum: General Help
---

### Post by ericzmeh on 2013-02-09
So I turned on my monitor today on my Ubuntu box had a black screen with what looked like a kernel dump of some kind.  Lots of stack traces and call traces.  Not sure, this has not happened before to me.  Before I start testing all my hardware in my box right away, I wanted to get some opinions from the community.  I found the message in /var/log in the system log that I had seen:

[IMG]http://i.imgur.com/y2olIf8.png[/IMG]

Basically just the "kernel:" messages.  I recently installed cifs-utils (yesterday) so not sure if that has something to do with it.  I am running Ubunto 12.10.

```
$ uname -a
Linux blackbox-desktop 3.5.0-23-generic #35-Ubuntu SMP Thu Jan 24 13:15:40 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by tgalati4 on 2013-02-10
It looks like a Chrome browser crash.  Perhaps you had a website tab that folded up, but Chrome kept running.  Look at your Chrome history and match it up with the time of the crash--2103 hrs.  What version of Chrome are you running and what website caused the crash?

---

### Post by ericzmeh on 2013-02-10
I cannot see any browser history with that exact time.  I remember there being a few tabs open when i had last left the machine.  Usually Chrome will give the "Awwwww snap" error upon crashing, but I do notice the Chrome flag now that you mention it.  I'm running version 24.0.1312.69 and Ubuntu shows no updates.  I'll just have to try and remember to keep the browser closed when the machine is idle and I'm AFK.  Thanks much for your feedback.

---

### Post by rnerwein on 2013-02-10
> **ericzmeh said:**
> I cannot see any browser history with that exact time.  I remember there being a few tabs open when i had last left the machine.  Usually Chrome will give the "Awwwww snap" error upon crashing, but I do notice the Chrome flag now that you mention it.  I'm running version 24.0.1312.69 and Ubuntu shows no updates.  I'll just have to try and remember to keep the browser closed when the machine is idle and I'm AFK.  Thanks much for your feedback.
hi
what i see in your post is: for me is this a kernel panic (protection fault). it's a bug in the kernel. chrome was just the process which was on-proc when it happen. 
cheers

---

