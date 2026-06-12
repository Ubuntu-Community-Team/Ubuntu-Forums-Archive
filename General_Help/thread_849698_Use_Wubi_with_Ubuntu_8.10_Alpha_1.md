---
title: "Use Wubi with Ubuntu 8.10 Alpha 1?"
date: 2008-07-04
forum: General Help
---

### Post by MrMatt on 2008-07-04
Hey guys,

just looking to use Ubuntu 8.10 Alpha 1 with Wubi.

I have downloaded the ISO (intrepid-alternate-amd64.iso), but I do not know how to force Wubi to use it?

Thanks
Matt

---

### Post by ago on 2008-07-04
I haven't started working on Intrepid yet, will be ready in the coming weeks.

---

### Post by flamelab on 2008-07-04
Could we try dist-upgrade to Intrepid ?

Do we need any APT-Pinning ? Or just a dist-upgrade ?(update-manager -d)

---

### Post by ago on 2008-07-04
Still a bit early for that

---

### Post by MrMatt on 2008-07-05
> **ago said:**
> I haven't started working on Intrepid yet, will be ready in the coming weeks.

what I mean is, I've been able to trick Wubi into using Ubuntu based distro's before, by just turning off the MD5 check, and starting it downloading, closing Wubi, using that file name on the ISO of the distro I want to use, then start again without MD5 check and it worked...

but for some reason, MD5 is forced in the new version of Wubi?

reason being, I like trying out the new versions of Ubuntu without going through all the usual hassle, and, I was able to use the 8.04 alphas and betas with earlier versions of Wubi.

---

### Post by ago on 2008-07-05
> **MrMatt said:**
> 
but for some reason, MD5 is forced in the new version of Wubi?

More likely is the version check that fails, you need to recompile wubi changing the items in /data and in particular settings.nsh and isolist.ini. Look at the log  in your user temp folder.

---

### Post by MrMatt on 2008-07-05
Alright, I don't really have any idea how to do that :(

any hints/tips?

or maybe an ETA as to how long it might be before Wubi supports it without me messing around in it?

---

### Post by ago on 2008-07-05
I am off for a week, I'll have a look after that. Shouldn't be too difficult though.

---

