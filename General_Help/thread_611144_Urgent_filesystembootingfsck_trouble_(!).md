---
title: "Urgent filesystem/booting/fsck trouble (!)"
date: 2007-11-12
forum: General Help
---

### Post by SomeLuser on 2007-11-12
Simply put:
I am continually (manually) rebooting my system to be greeted by 10 minutes of fsck trying to check my filesystem, which it has declared to have errors. So it hangs after 27.9%, and I have to reboot it. So I'm greeted by fsck (an on and on)

More:

[rant] For one thing, I'm quite angry that I was forced to run fsck. It hung, I rebooted, and now this whole mess is here. There should be an option to op out of this forced fsck. [rant\]

If you're wondering how I've been able to type this, I'm just using the computer next door.

I'm on to the 7th fsck already, and it has yet again come to a halt at 27.9%...

I tried recovery mode once, same reaction...

What can I do? I have some backups, which I put in place when I upgraded to Gutsy, and the only thing I can think of is perhaps going in through livecd to retrieve them. But they're like 10gb for one thing, and I haven't any mobile storage devices anywhere near that large.

I extend a plea of support to the Ubuntu Forums commmunity.

---

### Post by SomeLuser on 2007-11-12
Ummm... please?

---

### Post by dacap06 on 2007-11-12
This is MOST unusual behavior!  I have only seen fsck in an infinite loop like this when there has been some sort of hardware failure, not that I have seen everything.  I'd recommend booting from the live CD then doing the following:

First, boot into memcheck and run it for at least an hour.  If you have no errors, then ...

Second, boot into Ubuntu running from the live CD.  As root from a command line run fsck manually on your hard disk, one unmounted partition at a time.  Use verbose output (-V option) and interactive repair (-r option) as well so you can figure out what is going on.  It may be you have some bad blocks on your disk.  

If you find no hardware error and fsck can't fix the problem, you may need to force a mount, copy off the data that's still accessible, then format the offending partition.  Please document what you end up doing.  It could help others.

Don't give up hope!

DaCAP

---

### Post by atlfalcons866 on 2007-11-13
did you get an error code when fsck exited?

---

