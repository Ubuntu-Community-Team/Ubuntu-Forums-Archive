---
title: "Can't install .rpm because of key error"
date: 2008-04-28
forum: General Help
---

### Post by Griff on 2008-04-28
I'm trying to install a .rpm and I get this error.  I've tried a couple different rpms for a few different versions and I always get a similar error:

dsniff-2.4_0.1.i586.rpm: Header V3 DSA signature: NOKEY, key ID 58857177

Don't worry.  This is for monitoring my own network. :P

-Griff

---

### Post by oskar2000 on 2008-04-28
dsniff 2.4b1 is in the repos.
Why do you want to install an rpm?
And if you need this exact package, why don't you use alien?

---

### Post by Monicker on 2008-04-28
> **oskar2000 said:**
> dsniff 2.4b1 is in the repos.
Why do you want to install an rpm?
And if you need this exact package, why don't you use alien?

I was wondering that too.  Besides, dsniff is kind of outdated.

Ettercap.  ;)

---

### Post by Griff on 2008-04-28
> **oskar2000 said:**
> dsniff 2.4b1 is in the repos.
Why do you want to install an rpm?
And if you need this exact package, why don't you use alien?
It's actually opensuse I'm trying to install it on, which is rpm based.  I didn't mention this because the error didn't sound platform dependent.  I posted here and not a suse forum because
(1) I'm on ubuntu 90% of the time
(2) These forums are much more active
> **Monicker said:**
> I was wondering that too.  Besides, dsniff is kind of outdated.

Ettercap.  ;)
All I wanted from the dsniff suite is arpspoof.  Does ettercap have a similarly functioning program?

Thanks,
Griff

---

### Post by oskar2000 on 2008-04-30
So you did rpm -Uhv dsniff...rpm?
Even if it does work... you're getting yourself into dependency hell. You should find a repository that has the package.

---

