---
title: "Problems after upgrade"
date: 2014-04-02
forum: General Help
---

### Post by ballistic turtle on 2014-04-02
Good to know -_-
I'm back after many months of not touching Ubuntu and immediately into problems. Got the cannot find GLDR on any devices error. Fixed that. Then upgraded to 12.1, a process that started about 3 or 4 hours ago. Then it crashed when it was supposed to restart so I force quit (I'd been waiting 3 hours to see 12.1 is like). Getting /tmp is not ready yet error. And now it won't even boot in, it's just frozen on black screen. Get your act together Ubuntu, tired of your games, probably why I stopped using it in the first place. It basically appears to hard freeze so I have to hard reset it (which I've done twice now) and am still waiting to boot in.

This is why you're not a major player yet, but you got potential, but it's basically frozen on a black screen again so I'm just going to boot into Windows 7.

Any way to get Ubuntu to start?

---

### Post by monkeybrain20122 on 2014-04-02
Well 'upgrade' is a bad idea. I always do clean install.

---

### Post by ballistic turtle on 2014-04-02
Wish I'd known beforehand :(
Since this upgrade of 12.04 to 12.1 is broken, what's a good version to go with?

---

### Post by QIII on 2014-04-02
Is there a particular request for help here?

12.10 reaches EOL in two or three weeks, so it might not even be worth trying to sort it out.

---

### Post by mörgæs on 2014-04-02
> **ballistic turtle said:**
> what's a good version to go with?

Depends on your hardware. Please post a detailed description.

---

### Post by QIII on 2014-04-02
> **ballistic turtle said:**
> Wish I'd known beforehand :(
Since this upgrade of 12.04 to 12.1 is broken, what's a good version to go with?

The upgrade did not go well for this user.  That does not mean it is universally broken.  

Again, however, 12.10 reaches EOL this month so there is little use in doing it.

Clean reinstalls are less likely to be problematic, but many people have absolutely no problem whatsoever with upgrades.

Failing to uninstall proprietary drivers before upgrading seems to be the ost common source of problems.

---

### Post by ballistic turtle on 2014-04-02
> **QIII said:**
> Is there a particular request for help here?

12.10 reaches EOL in two or three weeks, so it might not even be worth trying to sort it out.

Yes, last sentence in the first post. How to get the current install to start, it always crashes on black screen after I tell it to do standard boot. Failing that, what version can I replace it with using Wubi?

Hardware:
Intel i5 2410M
HD Graphics 3000
500GB HDD
3GB RAM

I have a far more powerful gaming rig, but I don't run what I class as experimental software on it, my laptop is the test rig :P
Intel i5 4570
GTX 760
4TB HDD (2 x 2 TB)
16GB RAM

EDIT: Okay, it may not be broken for everyone, but in my experience it's had quite a few problems from the day I put it on (it even broke itself without me even using it, see the GLDR thing I mentioned)

---

### Post by 23dornot23d on 2014-04-02
> 
Since this upgrade of 12.04 to 12.1 is broken, what's a good version to go with?                 


14.04 is due out on the 17th April ....... might be worth installing it fresh in a clean partition alongside what you already have and pull any files in that you may
need once you have done it ......... this works for me as I keep a few versions of linux running and have a place where my files reside and can be
accessed from any version of Linux that I wish to run .......

But sometimes its best to try CDs out and see which works best for your hardware ......... or run 2 versions alongside one another if you have the room
on your drive for them ..... 40 gig for each is usually plenty ..... can be less - but I find this to be a good size for my own systems.

( Just seen wubi - install ........ my advice above is for proper installs - not sure how wubi works as I never used this type of install )

---

### Post by monkeybrain20122 on 2014-04-02
> **QIII said:**
> The upgrade did not go well for this user.  That does not mean it is universally broken.  

.

It doesn't go well for many users if you check the threads here. 

Even if it works it would take several hours. 

When new users are advised to 'upgrade' they are never told the caveats. For examples: it is only expected to work if you keep the box in a vanilla state. If you have made modifications like installing from ppas or proprietary drivers upgrade is likely to break (I can reinstall several times over for the time I need to spend to reverese all the changes I have made in order to have a fair shot at a successful upgrade) ; since it takes a long time during which many things can go wrong, say you may lose your internet momentarily during upgrade (maybe bad wifi connection)..then you are left with a broken box.

---

### Post by QIII on 2014-04-02
Without more information, it would be difficult to say how to get it to start.  Wubi was never intended as a long term solution.  In fact, the developers have themselves started to recommend against it -- and it really isn't suitable for Windows 8 for those who run that.

---

### Post by mörgæs on 2014-04-02
Wubi is deprecated. If you have Windows your best option is a real dual boot. 
Your hardware is strong enough to run any of the 13.10 Buntus. If you want stability you should stay with 13.10 for as long as it's supported.

---

### Post by monkeybrain20122 on 2014-04-02
Didn't realize that it was Wubi. Well that is not even really using Ubuntu in my view, and I wouldn't be surprised that it works poorly.

---

### Post by QIII on 2014-04-02
> **monkeybrain20122 said:**
> It doesn't go well for many users if you check the threads here. 

That's a phenomenon known as "referral bias" and can lead to conclusions based on a logical fallacy known as an "argument from silence".

People come here when they have problems, not to complain when things go right.  We do not now the percentage of each as a function of all Ubuntu users, so we can derive no definitive conclusion.  That's the problem with looking around the internet and concluding that "everyone has this problem."

---

### Post by monkeybrain20122 on 2014-04-02
> **QIII said:**
> That's a phenomenon known as "referral bias" and can lead to conclusions based on a logical fallacy known as an "argument from silence".

People come here when they have problems, not to complain when things go right.  We do not now the percentage of each as a function of all Ubuntu users, so we can derive no definitive conclusion.  That's the problem with looking around the internet and concluding that "everyone has this problem."

Well do you have a way to adjust for the referral bias, say Tobit (actually selection bias)? If not then I would say some data is better than no data at all. You cannot assume that it all goes well if people don't come to the forum. Maybe they just ditch Ubuntu, or maybe they are still running 8.04. you never know.

But I didn't just base my argument on forum threads. I also proposed reasons why upgrade is likely to fail based on the very mechanism itself,--it is a time consumming, complex and fragile process.

---

