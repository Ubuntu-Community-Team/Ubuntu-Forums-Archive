---
title: "Are Ubuntu and Debian really forked?"
date: 2008-03-07
forum: General Help
---

### Post by miju on 2008-03-07
How can I make sure I have the latest and greatest (stable/working) Debian, while continuing to use Ubuntu?:confused:

---

### Post by wolfen69 on 2008-03-07
are you dual booting ubuntu and debian?

---

### Post by miju on 2008-03-07
no, I'm not.

---

### Post by disturbedite on 2008-03-07
> **miju said:**
> How can I make sure I have the latest and greatest (stable/working) Debian, while continuing to use Ubuntu?:confused:
use hardy heron.  but its not recommended cuz its unstable.  its only recommended for experienced users.

---

### Post by jago25_98 on 2008-03-07
Actually I think I understand your question.

Yes they are different because they use different versions of software, and I doubt that HardyHeron and any of the debian releases match much.

Even if you had a 90% match you couldn't get it to work.

If you want you can install debian on one partition, ubuntu on another and share the /home directory, and maybe /var too. You can then chroot into either. You can also mess about with symlinking various directories. But with disk space as it is these days why not just install both

---

### Post by miju on 2008-03-07
> **jago25_98 said:**
> Actually I think I understand your question.

Yes they are different because they use different versions of software, and I doubt that HardyHeron and any of the debian releases match much.

Even if you had a 90% match you couldn't get it to work.

If you want you can install debian on one partition, ubuntu on another and share the /home directory, and maybe /var too. You can then chroot into either. You can also mess about with symlinking various directories. But with disk space as it is these days why not just install both

thanks, that answers much of my question. but why did ubuntu fork from debian so much? Is that true even if you use the extended package set from multiverse and the others? :confused: 

why did they break deliberately our ability to download and install the majority of debian packages?:mad:

---

### Post by lswest on 2008-03-07
Honestly, the majority of debian packages DO work for Ubuntu, they just require other dependencies than what is pre-installed with Debian.  Trust me, i've used both OSes, most programs working in one will work in the other.

---

### Post by edm1 on 2008-03-07
When they say Ubuntu "forked" from Debain, it means that when Ubuntu was first developed they used Debian as a base to start from. Since then they are developed individually and independantly of each other...but of course have similarities because they started as the same thing.

Just like humans and apes are much the same because we evolved from a common ancestor (if you believe in evolution).

---

### Post by fululian on 2008-03-07
> **edm1 said:**
>  (if you believe in evolution) 

oh come on, don't. really, just don't. not here, not in these forums. thank you.

---

### Post by edm1 on 2008-03-07
was trying to be PC but i guess it didnt work, lets hear no more about it.

---

### Post by Oldsoldier2003 on 2008-03-07
> **lswest said:**
> Honestly, the majority of debian packages DO work for Ubuntu, they just require other dependencies than what is pre-installed with Debian.  Trust me, i've used both OSes, most programs working in one will work in the other.

plus the Debian packages are usually a bit more stable, having gone through a longer pre release test cycle. you could say Ubuntu is bleeding edge Debian lol!

---

### Post by ubuntu-freak on 2008-03-08
> **edm1 said:**
> When they say Ubuntu "forked" from Debain, it means that when Ubuntu was first developed they used Debian as a base to start from. Since then they are developed individually and independantly of each other...but of course have similarities because they started as the same thing.

Just like humans and apes are much the same because we evolved from a common ancestor (if you believe in evolution).

 
They still take snapshots of Debian to make Ubuntu actually. They rely on Debian, and most core Ubuntu developers are still active Debian developers.
 
Nathan

---

### Post by disturbedite on 2008-03-09
> **jago25_98 said:**
> Actually I think I understand your question.

Yes they are different because they use different versions of software, and I doubt that HardyHeron and any of the debian releases match much.

if you understood the package inclusion process (such as syncing) you'd realize that using the latest unstable release (HH in this case) is the closest way to get the same versions of debian packages in ubuntu.

no thats not exactly the same as debian, obviously, but as i said, its the closest you can get on *ubuntu.

---

