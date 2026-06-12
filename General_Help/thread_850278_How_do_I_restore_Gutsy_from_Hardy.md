---
title: "How do I restore Gutsy from Hardy?"
date: 2008-07-05
forum: General Help
---

### Post by jws957 on 2008-07-05
I recently upgraded to 8.04, kernel 2.6.24-19
I am experiencing the lock-ups that are widely reported and want to go back to 7.10 (never had any problems with that version).
I am running on an AMD 64-bit desk-top, no wireless.

What is the cleanest way to go back?

Is there a fix for this on the way and I should wait?

---

### Post by Tomatz on 2008-07-05
> **jws957 said:**
> I recently upgraded to 8.04, kernel 2.6.24-19
I am experiencing the lock-ups that are widely reported and want to go back to 7.10 (never had any problems with that version).
I am running on an AMD 64-bit desk-top, no wireless.

What is the cleanest way to go back?

Is there a fix for this on the way and I should wait?

Reinstalling is the only way back TMK :(

Sorry.

---

### Post by Kevbert on 2008-07-05
If you only have lockups with Firefox you could try downgrading to FF 2.0.0.15.

---

### Post by coolaj86 on 2008-07-05
But before you reinstall, try creating a new user (Sys > Admin > Users & Groups) and logging in as the new user.

If you don't experience those problems as the new user you may be able to change a few settings on your main account and have everything run just fine.

Let me know how a new user works for you and I'll give you some other hints after.

---

### Post by Victormd on 2008-07-05
> **jws957 said:**
> I recently upgraded to 8.04, kernel 2.6.24-19
I am experiencing the lock-ups that are widely reported and want to go back to 7.10 (never had any problems with that version).
I am running on an AMD 64-bit desk-top, no wireless.

What is the cleanest way to go back?

Is there a fix for this on the way and I should wait?

The only way to go back is through a fresh install. Did you upgrade to Hardy via update manager or did you do a fresh install?
If you upgraded through update manager, that could explain a few of the freeze ups. I've read several threads where people upgraded this way and experienced problems (myself included) and after a fresh install of hardy, everything was fine, so if you're going to do a fresh install, install hardy again and see if you experience the same problems.

---

### Post by kevdog on 2008-07-05
Hardy fresh installs gives lockups.  Its possible however to compile an older vanilla kernel version (the one used in gutsy -- you would have to find that kernel version number), compile it, and then try to boot into this kernel in Hardy.  That would probably work if you don't want to do a complete install of Gutsy.

---

### Post by jws957 on 2008-07-05
I created a new user and after about 5 hours, no problems.  Can you let me know what settings changes to existing users may solve the problem?  Thanks!!

---

### Post by coolaj86 on 2008-07-05
I've been answering that problem a lot lately so I decided to put a page on the wiki instead of retyping the answer each time:

[https://wiki.ubuntu.com/CommonUpgradeProblems](https://wiki.ubuntu.com/CommonUpgradeProblems)

Let me know if that is clear enough for you.

:-D

---

### Post by Tomatz on 2008-07-06
:popcorn: for you ;)


That will save new users some hasstle.

---

### Post by jws957 on 2008-07-06
Unfortunately, it locked on my test user account later.  So..here goes back to 7.10 - very disappointing.  Thanks anyway, CoolAJ86!

---

### Post by Tomatz on 2008-07-06
> **jws957 said:**
> Unfortunately, it locked on my test user account later.  So..here goes back to 7.10 - very disappointing.  Thanks anyway, CoolAJ86!

It is probably the gpu drivers causing the lockups (which can happen after an upgrade). What graphics card are you using?

---

### Post by TonyGould on 2008-07-06
> **jws957 said:**
> I recently upgraded to 8.04, kernel 2.6.24-19
I am experiencing the lock-ups that are widely reported and want to go back to 7.10 (never had any problems with that version).
I am running on an AMD 64-bit desk-top, no wireless.

What is the cleanest way to go back?

Is there a fix for this on the way and I should wait?

I have 3 ubuntu installs, 2 laptops (Intel 32 bit installs) and a desktop (AMD 64 bit install). I had v severe problems with random hangs on the latter. I raised it on this thread, [http://ubuntuforums.org/showthread.php?t=848712](http://ubuntuforums.org/showthread.php?t=848712), and there are some suspiciouns about -19, apparently because of a new scheduler introduced (I'm not expert on this).

In any case I'm running the -18 kernel on that machine now, and have never experienced random hangs with it. As soon as I upgraded to -19 I had frequent random hangs, but unfortunately only realised it several weeks in.

I suggest it's worth you downgrading to the -18 kernel before abandoning hardy altogether, -- or you could try the test kernel that the person on that thread recommended, but I experienced some (repeatable, non-random) hangs with that.

ATB,

Tony.

---

