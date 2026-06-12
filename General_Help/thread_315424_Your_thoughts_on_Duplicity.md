---
title: "Your thoughts on Duplicity"
date: 2006-12-09
forum: General Help
---

### Post by linuxbun on 2006-12-09
Ever since I discovered this neat lil tool, since day 1 I have been impressed. Encrypted backups locally & over network which is also bandwidth efficient, what more could a girl want (First one to call me a geek gets a slap :mrgreen: ).

Before discovering duplicity I was having to encrypt volumes, something that wasn't very efficient and not something I could do over the network to a windows server.

Atm only 1 copy of my documents are encrypted (which are stored on a mates server). However, as I have quite a few, erm, how can I put this, saucy snaps? lol I am seriously debating to backup ALL my docs locally with duplicity.

My only concern is it's stabillity. I have read that it's not yet stable and is not to be relyed upon (I also hear that the developer has stopped developing it? Why, it's such a good thing!!). But hell if it works, surely it's safe? I'm just basically wondering (from any long term users of duplicity) have you had any problems recovering your backups?

Would appreciate your feedback on this issue, ta :D

---

### Post by stylishpants on 2006-12-09
I think the unique strength of duplicity is that it is does *incremental* encrypted backups.  

As you stated, the downside is that it is no longer maintained.  It can be tricky to figure out what is going wrong when it breaks.  Right now, I'm having to trace through the code to try to figure out why I suddenly can't do a restore.  This sucks, and would be less likely to happen if it was an active project with a healthy community. 

I am using it to back up a large, private source code repository to a remote web location where I don't have root.  My source code repo is currently about 600 MB, but I can store deltas for the last 5 days worth of code changes for just a few more MB, instead of 600 MB for each day.  Each night, only the new delta is sent over the network, which minimizes bandwidth.

For a collection of pictures or music, the incremental aspects aren't important, so I would prefer to use something that is better supported, such as rsync (combined with an encryption tool, if necessary.)

---

### Post by linuxbun on 2006-12-09
> **stylishpants said:**
> such as rsync (combined with an encryption tool, if necessary.)

But that doesn't encrypt the data does it? That just encrypts it during transfer?

I really am surprised that this isn't an ongoing project, duplicity to me is the sweetest thing that I've discovered since making the switch to linux.

Is it not possible for someone else to take it over? It just seems a real waste when this program has so much potential :confused:

---

### Post by jtc on 2007-01-16
Well, if you want to use rsync while having the data on the receiving end encrypted I guess you could always send your files through EncFs first. Since EncFs encrypts each file separately rsync only has to upload those files which has changed.

---

### Post by jtc on 2007-04-24
> **linuxbun said:**
> But that doesn't encrypt the data does it?I really am surprised that this isn't an ongoing project, duplicity to me is the sweetest thing that I've discovered since making the switch to linux.

Is it not possible for someone else to take it over? It just seems a real waste when this program has so much potential :confused:

Well, it seems as if Duplicity now has a new maintainer.

[http://lists.gnu.org/archive/html/duplicity-talk/2007-04/msg00025.html](http://lists.gnu.org/archive/html/duplicity-talk/2007-04/msg00025.html)

---

### Post by Steve413z on 2008-05-23
duplicity is awesome

---

