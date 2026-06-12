---
title: "Forced fsck: Why is mounting harmful?"
date: 2008-07-04
forum: General Help
---

### Post by mudd1 on 2008-07-04
Hi there!

I wonder why a fsck is forced after a file system got mounted x times. This implies that the act of mounting a FS is harmful in itself. I can hardly believe this. Neither can I believe that leaving my computer switched off for a prolonged period of time is that damaging to its FS. Maybe running a FS bears the potential of errors being introduced or *not* unmounting it might damage it, even for journaling file systems. But then a fsck should be forced after a certain total running time or when mounts-unmounts > x. This x might be much smaller than the default 30 times of regular mounts, as might the total running time threshold be much lower than the normal timeout.

But then I'm not a file system expert so please enlighten me someone why these primitive changes (adding up the run times and decreasing the mount counter right before umounting) are not done and the system we all know and hate is used instead.

Many thanks in advance,

Christian

PS: I hope this is the right sub-forum to post this in. I'm a little bit confused by the structure.

---

### Post by chrisccoulson on 2008-07-04
FSCK can be scheduled to run after a certain number of mounts have passed without a check, or a certain period of time has passed without a check. The tune2fs command can be used to change these limits.

Regular filesystem checks are advised as they might catch small errors due to kernel / filesystem driver bugs or other hardware problems (before these errors cause you a serious problem), and might provide an early warning of failing hardware.

---

### Post by lisati on 2008-07-04
I think I  get it: even using your computer contributes to "wear and tear".

My understanding is that a "regular" fsck is intended as part of normal security, to help check that your system is in order, very loosely analogous to running a defrag in Windows even when it's not strictly needed.

---

### Post by mudd1 on 2008-07-04
> **chrisccoulson said:**
> Regular filesystem checks are advised as they might catch small errors due to kernel / filesystem driver bugs or other hardware problems (before these errors cause you a serious problem), and might provide an early warning of failing hardware.

If these are the only reasons causing FS errors, then not only is this forced fsck for everyone IMO clearly an overreaction in times of S.M.A.R.T HDDs but also the ext3 module is buggy as hell :)

> **lisati said:**
> 
even using your computer contributes to "wear and tear".


Sure. My point is that then the time when a fsck is forced should depend on the "wear and tear", not on the time since the last fsck (computer off or not) or the mount count (might be correlated to wear, but no causal dependency I can see).

Or more generally put: If a broken FS is potentially caused by x, then the fsck should depend on x, not y. Even if y and x are correlated. This doesn't hold true if x is hard to measure but y isn't. This is not the case here though.

---

### Post by txcrackers on 2008-07-04
fsck detects *and repairs* problems, if needed. Yes, the interval is somewhat arbitrary, but considering it's been tweaked and refined for over a decade might be an indication that these defaults have been pretty well scrutinzed. Or maybe not - it may be "traditional." In any case, there's no harm in leaving the defaults and having some piece of mind that the system is looking out for itself... :wink:

---

### Post by mudd1 on 2008-07-05
> **txcrackers said:**
> fsck detects *and repairs* problems, if needed. Yes, the interval is somewhat arbitrary, but considering it's been tweaked and refined for over a decade might be an indication that these defaults have been pretty well scrutinzed. Or maybe not - it may be "traditional." In any case, there's no harm in leaving the defaults and having some piece of mind that the system is looking out for itself... :wink:

Well, the harm would be that I'm thinking twice about switching off my computer because every time I do draws that dreaded waiting nearer. If this is just because of some "traditional" heuristic that could be changed without harm, then it should be done.

Moreover, if my theory is true that the mount count is just a bad measure, then you can tweak and refine the threshold as long as you want without ever doing The Right Thing, let alone for everyone (laptops, desktop computers, servers... all have very different reboot frequencies and switch-off periods but use the same heuristic per default).

And then I just don't feel good about systems that don't do things the best way possible :)

---

### Post by txcrackers on 2008-07-05
> **mudd1 said:**
> Well, the harm would be that I'm thinking twice about switching off my computer because every time I do draws that dreaded waiting nearer. 

Uh, why is it "dreaded?"

fsck hardly takes any time at all when it runs and, as noted, it's not that often unless you're rebooting your system ten times a day. (If you are, then I'd be more worried about the *physical* wear and tear your placing on the system components.)

---

### Post by mudd1 on 2008-07-05
> **txcrackers said:**
> Uh, why is it "dreaded?"

fsck hardly takes any time at all when it runs

Either your hard disk is much smaller or much faster than mine. fsck takes ages for me. That's why I'm so annoyed by it. But that's not the main reason why I asked the questions I did and so you don't have to argue against that. I asked out of curiosity and out of principle: If it can be done better, why not do it? If it can't be done better, what did I get wrong? That's what I'm interested in, not in some argument over whether fsck is bad or annoying or whatever.

---

### Post by lightstream on 2008-07-05
> **mudd1 said:**
> Either your hard disk is much smaller or much faster than mine. fsck takes ages for me. That's why I'm so annoyed by it. But that's not the main reason why I asked the questions I did and so you don't have to argue against that. I asked out of curiosity and out of principle: If it can be done better, why not do it? If it can't be done better, what did I get wrong? That's what I'm interested in, not in some argument over whether fsck is bad or annoying or whatever.

Well I do find it annoying, and it's because of this that the frankly shoddy way it determines if a check is needed is so irksome. OK now that Hardy lets you cancel the check once it's started, the inconvenience is much reduced, but still the underlying issue is still there.

mudd1 is completely right - number of mounts and/or time since last check are not directly related to a need to do another check. Obviously some people's machines are rebooted much more frequently than others', and some people's machines are simply not switched on for long periods while many people leave theirs on 24/7. Other people sometimes leave their machines on for a long time without rebooting, and sometimes boot frequently.

I really do think some better way of determining the need for a check should be used and mudd1's suggestions would certainly be a vast improvement at little cost.

Another thing that would greatly minimise the disruption once a check is decided upon would be for the system to perform the check during shutdown, not during start up.

---

### Post by Steveway on 2008-07-05
Normally an fsck should happen at every boot. But since fscking an ext filesystem takes a rather long time the devs decided to only do this about every 30 mounts.

---

### Post by vanadium on 2008-07-05
Feel free to adjust these settings. For my laptop, I disabled the mount count, but have the system checked once a month.

It is unwise to turn checking off alltogether. If a check during startup happens at an inconvenient time (you are just loading up that presentation in front of the audience, for instance), then you can cancel out since Hardy.

If you anticipate that a check will come shortly and you find you'd better do it right away to be past it, then you can force a check on the next reboot with the command

```

sudo touch /forcefsck

```

Then restart the system, and a check will be performed. The counters are reset so you are settled again for one month or 30 boots, according to your settings.

---

### Post by mudd1 on 2008-07-05
I guess I'm talking too theoretical here. What I kinda suggest (let's say I want someone to tell me whether or not it'd be a good idea):

Adding something like

```
tune2fs -C $((`tune2fs -l $DEVICE | grep '^Mount count' | awk '{print $3}'` - 1)) $DEVICE
```

to /etc/init.d/umountfs and/or /etc/init.d/umountroot (I didn't look too much into these files and yes I know that the above line would need a lot of refinement and that there isn't even a variable $DEVICE yet. I primarily want everyone to get the point.) or even into a script that wraps umount. Then once setting the maximum mount count to 5 (i.e. tune2fs -c5) or something like that.

Similarily the wrapper could read the "last mount time", let's call it LMT, in Unix time on unmounting and add ```
$((`date +%s` - LMT))
``` to a value stored in some file. Then when some threshold is reached &#8594; forced fsck and reset of mount count and the "value stored in some file". This threshold would be somewhat lower than the normal check interval (which is deactivated on Ubuntu BTW as it seems?).

---

### Post by danwood76 on 2008-07-05
The currunt system for fsck is fine IMO.
I have my lappy set to once a month and my desktop is default 22 mounts or whatever.
Your idea  (If I understand what your saying) would still result in pretty much the same thing as the time limit.

Its better to kinow that your system checks its disks every now and then without your input then to suddenly have data corruption on your / partition and linux doesnt load.

---

### Post by cariboo on 2008-07-05
mudd1 check out **man tune2fs**. You can set the count to whatever you want or disable it completely.

No need to come up with a script that duplicates processes that are already in place.

Jim

---

### Post by mudd1 on 2008-07-05
> **cariboo907 said:**
> mudd1 check out **man tune2fs**. You can set the count to whatever you want or disable it completely.

No need to come up with a script that duplicates processes that are already in place.


What do you mean? Can tune2fs decrease the mount count without reading it out before or is there even a switch for an automatic decrease on unmount? I can find neither, sorry :/

---

### Post by dcstar on 2008-07-05
> **mudd1 said:**
> Hi there!

I wonder why a fsck is forced after a file system got mounted x times. This implies that the act of mounting a FS is harmful in itself.
........

1: It is a good idea to run a filesystem check at regular intervals because there is no guarantee that a running OS can totally control everything that happens to a filesystem.

People can lose power and risk filesystem corruption, processes can crash and risk filesystem corruption, hardware can go faulty and risk filesystem corruption, power spikes can cause filesystem corruption etc. etc. etc.

This is an unavoidable reality of any computer system and the risk can be reduced by different filesystem types, but there is a trade off between performance and robustness and people decide to use a filesystem that is acceptable in both areas for the overall system requirements.

2: No, it implies no such thing. Doing a filesystem check is an extra overhead that is not necessary most times when mounting a filesystem, though it is a good idea to do it at some interval.

As stated by others, the "x times" is a default value for EXT2 filesystems that can be changed as you like. It was obviously chosen as a compromise value between mitigating risk (smaller value the better) versus not inconveniencing users (larger value the better).

---

### Post by mudd1 on 2008-07-06
> **dcstar said:**
> Doing a filesystem check is an extra overhead that is not necessary most times when mounting a filesystem, though it is a good idea to do it at some interval.

Thank you for your detailed reply but you did either not read or did not understand my other posts. If my bad English is the reason for the latter, I apologize. OTOH I tried bash instead of English and syntax and semantics were correct in this case. If anybody knows how it can be helped that nobody seems to understand my point and people keep treating me like a slightly retarded Linux newbie, please help me out.

---

### Post by VMC on 2008-07-06
mudd1,

Let's put this in another direction. Since your so concerned with 'fsck' and its lack of ability to perform artificial intelligence. 

How do you check your Windows (Mac, or other OS) file system?

Remember, 'fsck' is just a tool. Your the one behind the tool. Use it under your discretion.

---

### Post by mudd1 on 2008-07-06
> **VMC said:**
> 
Let's put this in another direction. Since your so concerned with 'fsck' and its lack of ability to perform artificial intelligence. 

Sure, because the two lines of shell code I wrote above are anywhere near AI techniques. I'm talking about using a better measure, not about Voodoo.

> 
How do you check your Windows (Mac, or other OS) file system?


I didn't touch any Windows system since I was a child. Back then it used to check every time you didn't do a proper shutdown. I know they have journaling now, too, but I really can't tell you any more about it. Why?

---

### Post by lightstream on 2008-07-10
Well mudd1 I get your point completely. He's not saying that disk checking is bad, and he's also not saying that mounting a disk ~is~ actually harmful.

He's just asking whether, given that disk checking is a good idea, a better way to determine when one is worth doing would be to count the number of 'unclean' shutdowns (ie power off without unmounting) and/or record roughly how long the system is actually running.

---

### Post by mudd1 on 2008-07-11
> **lightstream said:**
> Well mudd1 I get your point completely. He's not saying that disk checking is bad, and he's also not saying that mounting a disk ~is~ actually harmful.

He's just asking whether, given that disk checking is a good idea, a better way to determine when one is worth doing would be to count the number of 'unclean' shutdowns (ie power off without unmounting) and/or record roughly how long the system is actually running.

That's exactly what I was trying to say. Sorry if the thread subject was a bit too provocative.

---

### Post by Linder on 2008-07-11
It might actually be wiser. But I'm not sure "General Help" is the place to put such a suggestion. I wouldn't know where to put it though, I'm a forum noob :D


(And fsck-ing an XFS partition of over 250 Gb is REALLY fast, btw...)

---

### Post by mudd1 on 2008-07-16
> **Linder said:**
> It might actually be wiser. But I'm not sure "General Help" is the place to put such a suggestion. I wouldn't know where to put it though, I'm a forum noob :D

AOL. But I objected whether this is the right one myself and nobody told me a better place to put it or moved the thread over to another forum.

> 
(And fsck-ing an XFS partition of over 250 Gb is REALLY fast, btw...)

I'm using ext3. I had some *very* bad experiences with ReiserFS which made me wary.

---

