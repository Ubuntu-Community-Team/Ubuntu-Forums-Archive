---
title: "Ubuntu-Mate 14.04 LTS vs 15.04 (unofficial vs. official)"
date: 2015-06-11
forum: General Help
---

### Post by cogset on 2015-06-11
I just have to ask this: what are the differences, security-wise, between an official release such as Ubuntu-Mate  15.04 vs. an "unofficial" build like 14.04 LTS ? 
Do I have to think of it as less safe than the official version?
Or maybe it's not a security issue, but stability problems or update issues may eventually be expected?

---

### Post by QIII on 2015-06-11
Which unofficial 14.04 LTS build?

Ubuntu Mate before they became a recognized flavor?

Probably very little.

---

### Post by v3.xx on 2015-06-11
> Or maybe it's not a security issue, but stability problems or update issues may eventually be expected?

No security or stability issues that I know of.
One thing though.  Mate is being developed at what I consider to be a very fast pace.  14o4 is my main install and works fine, but there are many under the hood changes you won't see in this release.  IMO lots of good changes.  I am normally a 'LTS' advocate, but ..

So why have I not upgraded?  14o4 for me is up and stable and I don't want to mess with it.  But I also run Mate 15.10 and know what I'm missing out on (also ran 15.04 pre-release).

---

### Post by kerry_s on 2015-06-11
go for 15.04 it is more awesome than 14. i also think it's much stabler than 14 was, 14 i had issues with icons disappearing, it was slower, etc...

i have no issues in 15, the only major thing i did was swap mate-panel for xfce4-panel & i only did that because xfce4-panel has intelli hide for the panel, which i wanted to maximize my 10" 1024x600 screen on my hp mini netbook.

---

### Post by cogset on 2015-06-12
> **QIII said:**
> Which unofficial 14.04 LTS build?Ubuntu Mate before they became a recognized flavor?Yes, I actually meant  "unofficial" Ubuntu-Mate 14.04 LTS vs  "official"  Ubuntu-Mate  15.04 .

I hear the remarks about MATE being developed very quickly, and 15.04 being better ... but, I just can't stand non LTS releases, I've never installed one so far. 
Tried from a live CD, yes, to see what is what and have a glimpse of what may be coming, but I just don't like to i install for everyday use stuff that has to be replaced too quickly ;)

On the other hand, with 14.04 being the current Ubuntu LTS, the next official Ubuntu-Mate release won't be due any time soon, therefore I'll have to  either assume that Ubuntu-Mate 14.04 (although "unofficial")   is no riskier than a regular Ubuntu version on top of which I've added the MATE repo, or use 15.04...

---

### Post by cogset on 2015-06-14
Well, I've had a quick spin (live session) with 15.04  and it really looks (at first glance) more polished than  Ubuntu-Mate 14.04 ;) 
One thing that I've noticed is that it apparently uses systemd by default, something that I totally have to learn -unless I switch it back to upstart when I'll install it.

---

### Post by kerry_s on 2015-06-14
> **cogset said:**
> Well, I've had a quick spin (live session) with 15.04  and it really looks (at first glance) more polished than  Ubuntu-Mate 14.04 ;) 
One thing that I've noticed is that it apparently uses systemd by default, something that I totally have to learn -unless I switch it back to upstart when I'll install it.

hmm, i have both installed on mine.
perhaps systemd is default & upstart is backup ?

whats to learn, not exactly something you'll need to mess with.

---

### Post by cooleryawner on 2015-06-14
No difference other than just having an older version of Ubuntu and maybe an older version of MATE.

---

### Post by cogset on 2015-06-15
> **kerry_s said:**
> whats to learn, not exactly something you'll need to mess with.How to start/stop/disable services, to begin with? Besides, I'd just want to see what it does and how it does it.

---

### Post by cogset on 2015-06-16
> **kerry_s said:**
> hmm, i have both installed on mine.
perhaps systemd is default & upstart is backup ?


Sort of, here are more details:

[https://wiki.ubuntu.com/SystemdForUpstartUsers](https://wiki.ubuntu.com/SystemdForUpstartUsers)

> System Init Daemon

This has changed as part of the Ubuntu 15.04 devel cycle.

Ubuntu 15.04 (using Systemd by default):

    Systemd runs with PID 1 as /sbin/init.

    Upstart runs with PID 1 as /sbin/upstart. 

Prior versions (using Upstart by default):

    Upstart runs with PID 1 as /sbin/init.

    Systemd runs with PID 1 as /lib/systemd/systemd.
_______________________________________________________________

Switching init systems

If you are running Ubuntu vivid (15.04), you can easily switch between upstart and systemd at will since both packages are installed at present. [I]As of March 9 2015, _vivid was changed to use systemd by default, before that upstart was the default_.
[/I]


---

### Post by Buntu Bunny on 2015-06-16
Does anyone have any idea of when an official Ubuntu-Mate LTS will be released?

---

### Post by kerry_s on 2015-06-16
most likely next year.
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

