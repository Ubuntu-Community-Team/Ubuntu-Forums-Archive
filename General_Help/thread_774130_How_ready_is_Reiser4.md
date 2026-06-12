---
title: "How ready is Reiser4?"
date: 2008-04-29
forum: General Help
---

### Post by skymera on 2008-04-29
I've seen somethings online that compare EXt3 and Reiser4.

Seems Reiser 4 is very good, but is it stable to use?
I installed my system with EXT3 as i know its a rock solid FS.

Just quick question, wasn't sure where to post so i thought here. :)

Thanks.

---

### Post by OffHand on 2008-04-29
I would not use Reiser: [http://blog.wired.com/27bstroke6/2008/04/reiser-guilty-o.html](http://blog.wired.com/27bstroke6/2008/04/reiser-guilty-o.html)

---

### Post by skymera on 2008-04-30
ow.
I was thinking of using ReiserFS for a change but it lead to a sloww boot.
So im back at EXT3.

And that murder thing is old now.
Why judge a filesystem on his actions?
Im pretty sure the filesystem didn't inherit his murdering abilities.

Any **real** reason not to use it?

---

### Post by Archmage on 2008-04-30
> **skymera said:**
> Any **real** reason not to use it?

Please note that raiser4 (and ext4) are still in developement. So if you don't mind that it could be slow or you could lost your data, you could use it.

Most of us have important data, therefore we shouldn't use it.

---

### Post by sujoy on 2008-04-30
i am just sticking to ext3 for the moment, no matter my data is important or not i cant stand to reinstall it every now and then, and loose my config, i did try reiser4 once though and it seemed slow to response from cold compared to ext3, so i am back again

---

### Post by Loranga on 2008-05-07
As asked in another thread, how do I use reiser4 in Hardy?

---

### Post by articpenguin on 2008-05-07
> **Loranga said:**
> As asked in another thread, how do I use reiser4 in Hardy?

you have to compile a kernel and add andrew mortons -mm kernel. Reiser4 is not in the mainline kernel and i dont think it ever will be.

---

### Post by OffHand on 2008-05-07
> **skymera said:**
> 
And that murder thing is old now.
Why judge a filesystem on his actions?
Im pretty sure the filesystem didn't inherit his murdering abilities.

Any **real** reason not to use it?

It probably will not be developed anymore for a long time...

---

### Post by sokolovss on 2009-02-19
There are no support in ubiquity.

---

### Post by sokolovss on 2009-06-19
Reiser4 is rather stable. The main developer - Edward Shishkin said, thet FS is resdy to be included to the kernel (and also he said, that if send request now - it will be there) but he has no time to maintain the FS.

Also the last bug report was in 2006 and now more reports needed.

Maybe somebody could patch the kernel and make *.deb package, then also patch ubiquity and make something like reiserbuntu - fork from official.

I think many people will use it, but I have not enough knowledge to do it myself.

---

### Post by davidogg on 2010-08-11
> **sokolovss said:**
> Reiser4 is rather stable. The main developer - Edward Shishkin said, thet FS is resdy to be included to the kernel (and also he said, that if send request now - it will be there) but he has no time to maintain the FS.

Also the last bug report was in 2006 and now more reports needed.

Maybe somebody could patch the kernel and make *.deb package, then also patch ubiquity and make something like reiserbuntu - fork from official.

I think many people will use it, but I have not enough knowledge to do it myself.

I put up a recompiled Ubuntu kernel with Reiser4/full preempt here, but Ubiquity would still need patching to install to it.

[http://ubuntuforums.org/showthread.php?t=1548543](http://ubuntuforums.org/showthread.php?t=1548543)

---

### Post by AlphaLexman on 2010-08-11
This is an OLD post and anyone considering the validity of reiser MUST read the link in OffHand's post #2 in this thread. Really.

---

### Post by Monotoko on 2010-08-11
Again, you cant really judge the filesystem on his actions, I use reiser4 and have been for the past few years.

It is being developed by a team, just without reiser as head.

---

### Post by davidogg on 2010-08-11
> **AlphaLexman said:**
> This is an OLD post and anyone considering the validity of reiser MUST read the link in OffHand's post #2 in this thread. Really.

Yes, the guy murdered his wife and is in prison. The file system is unaffected.

This reminds me of that linux distro that refused to include Sendmail because "the author is a prominent homosexual"

---

### Post by AlphaLexman on 2010-08-11
> **davidogg said:**
> Yes, the guy murdered his wife and is in prison. The file system is unaffected.
He WAS the lead developer, the trend of the filesystem is on a downhill slide without him.

What would happen to Canonical if Stallman was in prison, or to the kernel if Torvalds was in prison?

It's devastating, and Reiser had no second-man to take over his work... my **guess** is it is destined to wash away and fail.

---

### Post by Monotoko on 2010-08-11
> **AlphaLexman said:**
> He WAS the lead developer, the trend of the filesystem is on a downhill slide without him.

What would happen to Canonical if Stallman was in prison, or to the kernel if Torvalds was in prison?

It's devastating, and Reiser had no second-man to take over his work... my **guess** is it is destined to wash away and fail.

I don't know about anyone else, but I think the kernal would defintly continue without Linus.

Daniel

---

### Post by bodhi.zazen on 2010-08-11
Can we please keep this thread on topic, ie the technical merits and stability of reiserfs4.

Why would one use reiserfs4 over ext4 or btrfs ?

---

### Post by Zeike on 2010-08-11
> **AlphaLexman said:**
> What would happen to Canonical if Stallman was in prison, or to the kernel if Torvalds was in prison?

Considering that neither Stallman (or Torvalds) is associated with Canonical... probably nothing.

Anyway, btrfs is coming along quite nicely if you want some of the features used by Reiser4.  If not, Reiser4 development is still going.

---

### Post by davidogg on 2010-08-11
> **AlphaLexman said:**
> He WAS the lead developer, the trend of the filesystem is on a downhill slide without him.

What would happen to Canonical if Stallman was in prison, or to the kernel if Torvalds was in prison?

It's devastating, and Reiser had no second-man to take over his work... my **guess** is it is destined to wash away and fail.

Stallman as in RMS?

umm... nothing. I'm not running HURD or Emacs as my OS.

Reiser4 is prime time and the patches continue.

---

### Post by davidogg on 2010-08-12
> **articpenguin said:**
> you have to compile a kernel and add andrew mortons -mm kernel. Reiser4 is not in the mainline kernel and i dont think it ever will be.

I heard bad things about the Reiser4 in the mm kernel, but it almost looks like satire so I don't know. People keep repeating what looks like it could be a troll or satire- the URL looks very suspicious:popcorn:;
[http://linuxhelp.150m.com/jews/saboteurs.htm](http://linuxhelp.150m.com/jews/saboteurs.htm)

Anyways, you can get the Reiser4 patch here and patch the Ubuntu kernels.
[http://www.kernel.org/pub/linux/kernel/people/edward/reiser4/reiser4-for-2.6/](http://www.kernel.org/pub/linux/kernel/people/edward/reiser4/reiser4-for-2.6/)

---

