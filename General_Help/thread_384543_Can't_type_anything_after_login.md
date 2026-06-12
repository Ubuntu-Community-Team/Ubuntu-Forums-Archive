---
title: "Can't type anything after login"
date: 2007-03-14
forum: General Help
---

### Post by ipudding on 2007-03-14
I'm using Kubuntu 6.10.

My problem is after I logged in my account. Keyboard doesn't work. But I create a new account and log in. I can use my keyboard normally. (Keyboard error on my account only.)

I can't type anything with my keyboard. Mouse is work. I think it must happend from some program that autorun with kde when i log in.

Please help me!
:confused:

---

### Post by gus sett on 2007-03-14
if you have access to the profile of the working account, you can compare it
to the non-working one.  You can look up *diff * in the *man* pages
to help compare text.  If you do not have too much vested in your account,
you can transfer what you want to salvage from it, remove the account and 
reconstruct it again. :wink: 

> **ipudding said:**
> I'm using Kubuntu 6.10.

My problem is after I logged in my account. Keyboard doesn't work. But I create a new account and log in. I can use my keyboard normally. (Keyboard error on my account only.)

I can't type anything with my keyboard. Mouse is work. I think it must happend from some program that autorun with kde when i log in.

Please help me!
:confused:

---

### Post by nautilus on 2007-04-19
And it's hit me too, suddenly.

I SSHed into the system and killed kaccess, and could suddenly type again.

How to disable this and avoid it happening again?

I'm not sure, the trick will be in editing a config such that kaccess won't startup anymore, unless of course you need it, in which case I'm not sure of a fix.

Once it's killed and you get into KDE, I suggest simply disabling it.

---

