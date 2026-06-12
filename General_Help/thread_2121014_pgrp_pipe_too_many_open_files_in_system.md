---
title: "pgrp pipe: too many open files in system"
date: 2013-02-28
forum: General Help
---

### Post by pwabrahams on 2013-02-28
I'm running 64-bit Kubuntu 12.10 on a Lenovo laptop.  Lately I've been having a problem with my system running very slowly -- hardly responding at all.  The message "pgrp pipe: too many open files in system" shows up in a terminal window, repeated several times.  (The terminal window was already open but nothing else was running in it.)  Firefox is running and I suspect it's somehow related to this behavior, but I'm not sure.  What might be the cause?

---

### Post by pbrane on 2013-02-28
This may help some:
[http://ubuntuforums.org/showthread.php?t=1961208]("http://ubuntuforums.org/showthread.php?t=1961208")

post #2 has some info and commands about open files.

---

### Post by pwabrahams on 2013-02-28
I've raised the limits on open files, as the post you referred me to suggested.  But I'm still concerned that the real problem is that some program is going wild with opening files.  I suppose time will tell if raising the limits helps at all.

---

### Post by matt_symes on 2013-02-28
Hi

> I've raised the limits on open files, as the post you referred me to  suggested.  But I'm still concerned that the real problem is that some  program is going wild with opening files.

So would i be  concerned. And don't forget, in Linux everything is a file (network sockets, pipes etc).

Increasing the file limits should help but i suspect that is just a sticking plaster on an underlying problem.

Maybe a utility like ```
losf
``` would help you trackdown which process(es) has those files open.

Any special software on the system ?

Kind regards

---

### Post by pwabrahams on 2013-03-02
The following message showed up in syslog, repeated many times:

Mar  2 18:40:03 Amanita kernel: [372994.826802] VFS: file-max limit 385409 reached

This problem popped up a week or so ago, so I assume that an erronous update is the cause.   But I still don't know what to do about it except logging out and logging back in again.

---

### Post by rnerwein on 2013-03-03
> **pwabrahams said:**
> The following message showed up in syslog, repeated many times:

Mar  2 18:40:03 Amanita kernel: [372994.826802] VFS: file-max limit 385409 reached

This problem popped up a week or so ago, so I assume that an erronous update is the cause.   But I still don't know what to do about it except logging out and logging back in again.
hi

if it happen again run: for i in [COLOR=#ff0000]`[/COLOR]ls -d /proc/[0-9]*/fd[COLOR=#ff0000]`[/COLOR]; do echo "----> $i [COLOR=#ff0000]`[/COLOR]ls $i | wc -l[COLOR=#ff0000]`[/COLOR]"; done > bla     # [COLOR=#ff0000]`[/COLOR]  this is a back-tick !

this gives you all /proc/[COLOR=#b22222]PID[/COLOR]/fd count. have a look in "bla" who is the delinquent (ps -ef | grep [COLOR=#b22222]PID[/COLOR]) using all the file-descriptors.
ciao

---

### Post by pwabrahams on 2013-03-16
I haven't managed to catch the problem at the right time yet.  But one observation: the problem seems to take a while to "ripen".  I left the machine overnight and came back in the morning to find it hung, with the error showing up in the previous syslog.

---

