---
title: "duplicate process running"
date: 2007-10-20
forum: General Help
---

### Post by Naegling23 on 2007-10-20
Im looking at my kde system guard, and noticing that I have duplicate processes running.  For example, there are 3 instances of python, two of avahi-daemon, 6 of something called getty.  Can I kill these duplicate processes, or should I just leave them running?

also, does anyone have a list of process that should always be running so that I can kill the unnecessary ones?

---

### Post by DagMan on 2007-10-20
Often python apps will just show up as python so for example if you have screenlets running, or maybe desklets as well but never looked to be sure, you have a python for each one.  Other python applications will do this too.
the gettty are your consoles when you hit ctrl-alt-f1 through f6 so this is normal
Not sure about the daemon, I don't have it or have previously disabled it.  It's a DNS server for within a network from the looks of it on google.  That must be why  I disabled it.  I don't think it would be there twice unless it was supposed to or unless you specifically asked it to be and then it would have to be something that didn't check for a previous instance of itself or whatnot.  Google it though, and decide if you need it or not.

---

### Post by Naegling23 on 2007-10-23
well thats good to know.  I just checked on the running processes, and saw a whole bunch of things, I wasnt sure if they were necessary, or improperly killed programs.  This all started when I upgraded to gutsy and reinstalled compiz.  I noticed that my cpu usage was abnormally high.  When I looked at the running processes, I had two different kde display (I cant remember what it was called exactly) programs running, one of them was 95%.  Killing it dropped my cpu usage down to normal, so I began to wonder if these other programs (none of them are using the cpu, they all register 0) are running in error, or if they are supposed to be running....I guess they are.

---

