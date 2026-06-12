---
title: "Dapper To Edgy"
date: 2006-11-04
forum: General Help
---

### Post by Kingfield on 2006-11-04
Hey, if i upgrade, am i likely to run into a lot of problems...? Also, Will all my already installed programs still run?

Thanks in advance

---

### Post by taurus on 2006-11-04
It looks like 50-50 whether it runs smoothly or not.  Some people have success while others run into some problems when they upgrade from Dapper to Edgy.  Of course, always back up your important files first before you try to upgrade your machine.  Here is the instruction on how to do it.

[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

---

### Post by Neobuntu on 2006-11-04
Do not do an upgrade yet! It's getting better every minute but a clean install is the way to go if you must have Edgy now.

Stay with Dapper if you are the least bit non-uber-geek. (regular person; "real people"; new user) 

I hate this situation as ANY release should be stable or not released IMHO. Regardless of name, policy or communication this release should have come out the gate better than it did for upgrading. It is NOT like the Dapper upgrade. Minor problems always accepted.

Once "Edgy" is clean installed you can view some easy fixes in the forums for things like Firefox 2.0 crashing.

---

### Post by s_h_a_d_o_w_s on 2006-11-04
YEs don't update! It's not worth the chance of a failed install. That's what happened to me. X broke, turns out there was a problem with xserver-xorg. I couldn't even reinstall it but one day i'll find a way to isntall xserver-xorg, 

sudo apt-get install xserver-xorg

yields demands for dependancies but it says they won't be installed. Re confusing.

Don't take the chance there is nothing wrong with Dapper, and i'm pretty sure you can just upgrade everything manually. :-)

---

### Post by Sef on 2006-11-04
> I hate this situation as ANY release should be stable or not released

Edgy is the testing distro; hence, it will tend to be unstable.

Dapper is the stable distro, so it will have software that is reliable, but not so up-to-date.

---

### Post by Kingfield on 2006-11-05
hmmm...... i guess i WONT upgrade after all. Thanks everyone.

---

### Post by zgornel on 2006-11-05
Edgy is pretty stable and everything works, provided that you backup your stuff (ideally separate /home partition) and do a fresh install. Plus it's a bit faster than Dapper but maybe it's just me.

P.S If Edgy is a testing distro, why bother with all the Knots, Alphas and RC's ?

---

### Post by jordilin on 2006-11-05
> **zgornel said:**
> Edgy is pretty stable and everything works, provided that you backup your stuff (ideally separate /home partition) and do a fresh install. Plus it's a bit faster than Dapper but maybe it's just me.

P.S If Edgy is a testing distro, why bother with all the Knots, Alphas and RC's ?

Yes, if you do a fresh install Edgy is very stable and everything works quite out of the box. And yes, it's faster than Dapper.

---

### Post by Neobuntu on 2006-11-05
Darn it! Not yet. It's not that much faster. Read what I said. Do not **UPGRADE** to it when you can do a **clean install** if anything(now; today). 

If you don't want to start over now or are non-technical then WAIT! You are not missing much.

I am using a successful Edgy UPGRADE right now, but I do NOT recommend it YET. It was a nightmare. All the good work of Edgy has been tainted IMHO because of this schizophrenic idea about it being "edgy" and not "LTS" but an official **STABLE** Six month **RELEASE**.

> P.S If Edgy is a testing distro, why bother with all the Knots, Alphas and RC's ?

Darn well said there zgornel.

Testing is not an official release and a finished release is not (or should never be) in testing. Minor fixes accepted.

What we have here is a switch from Six month releases to One every year and if this is the reality, then we should be forthcoming about it.

These speeches about "Edgy" and not being a "LTS" are pure BS. IMHO.

---

### Post by maniacmusician on 2006-11-06
eh. not really. 

The release cycle of Ubuntu is unique, so you can't treat it like everything else (ie; every release has to be rock solid stable). the LTS is the only one designed to withstand the test of time. The other releases are representative of the steps taken toward the next LTS. Edgy was the example of the under-the-hood improvements made to Ubuntu, whereas Feisty will be about cosmetic improvements. Edgy was not designed to say "Hey, come try this super stable OS," it was more like "Alright, one more step toward a better OS."

Why do you think the only supported upgrade paths are from LTS to LTS?

---

### Post by zgornel on 2006-11-06
Bottom line, If you're well with Dapper stick with it.

---

### Post by Kingfield on 2006-11-07
yeah, i dnt wanna lose my programs and stuff i guess - by the way can anyone recommend a good ipod manager for linux? amarok works okay?

---

### Post by zgornel on 2006-11-07
> **Kingfield said:**
> yeah, i dnt wanna lose my programs and stuff i guess - by the way can anyone recommend a good ipod manager for linux? amarok works okay?

I believe Automatix had some kind of software that managed that. Gtkpod or somethin. Check it out.

---

### Post by Kingfield on 2006-11-08
kk tyy

---

### Post by LxP on 2006-11-12
> **Neobuntu said:**
> All the good work of Edgy has been tainted IMHO because of this schizophrenic idea about it being "edgy" and not "LTS" but an official **STABLE** Six month **RELEASE**.

The official Ubuntu website does describe Edgy as a stable release.  I couldn't find a page where it was described as LTS.  Could you please elaborate?

> **Neobuntu said:**
> What we have here is a switch from Six month releases to One every year and if this is the reality, then we should be forthcoming about it.

Could you please tell me more about this decision to change from a six-monthly release cycle to a yearly cycle or provide some links so that I can read up on this change?  Does this mean that Feisty is due for release in October next year?

---

### Post by Neobuntu on 2006-11-14
I said Edgy is NOT an LTS and the point being, why is non-LTS, (but RELEASED) unstable anyway? In other words, saying it's not an LTS (and saying that's why it's unfriendly) is lame.

One year clarification: I am suggesting it is LIKE we have moved to one year stable releases (for all practical purposes) but the powers that be have NOT confessed it. Never am I suggesting that I have read notice of it.

The question is, will it stabilize? Yet a better one is, will we allow this to happen again? What can we do to prevent massive user fixes; on ANY newly released version? 

How about a better prepared provision to quickly re-release troublesome(using some indicator) releases. This mainly has to do with the installer and/or upgrade methods as everything else is a simple "upgrade" (if you have broadband).

---

