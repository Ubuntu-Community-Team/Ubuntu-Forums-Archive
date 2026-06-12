---
title: "open office problem"
date: 2007-03-27
forum: General Help
---

### Post by pepa on 2007-03-27
Hi,

I recently installed ubuntu 6.10 on my thinkpad T60, but after I installed everything and configured everything I found out that open office didn't work.

running ooffice at the command line gives the following error:

** (process:7019): WARNING **: Unknown error forking main binary / abnormal early exit ...

I did some googleing, which showed others with the same problem, but the solutions did not fix my problem.  I've tried reinstalling open office and checked my xorg.conf file to make sure the screen is setup right.


anyone here having the same problem?? or know a fix for it?

Cheers,

---

### Post by acormack on 2007-03-28
If the problem only occurs in Open Office then I wouldn't have thought your xorg.conf would be the problem.

Do any other applications misbehave?

What version of Open office are you running?

Did you install it using Adept?  If so why not try uninstalling and downloading direct from [www.openoffice.org](www.openoffice.org)


Alec

---

### Post by pepa on 2007-03-29
> **acormack said:**
> If the problem only occurs in Open Office then I wouldn't have thought your xorg.conf would be the problem.

Do any other applications misbehave?

What version of Open office are you running?

Did you install it using Adept?  If so why not try uninstalling and downloading direct from [www.openoffice.org](www.openoffice.org)


Alec

Everything else seems to run really well, no problems what so ever.


running  ooffice --version gives me:

This is OpenOffice.org built with ooo-build-2.0.4

It was installed by default by Ubuntu installer, yeah I could try downlading from the site, but will this leave my system in an inconsistent state? I've had problems in the past (awhile back) where installing stuff that's not from the repository meant that the package manager couldn't see it so I had no way of un-installing...but that was mandrake :P 

anyway I'll give it a go and see. In the mean time if you (or others) have anymore suggestions I'm happy to hear it!

thanks for replying :D

---

### Post by aldeby on 2007-05-28
If you installed SCIM imput for non latin languages this fix done the job for me: 
> [http://ubuntuforums.org/showpost.php?p=2568329](http://ubuntuforums.org/showpost.php?p=2568329)
Hope it helps. It has been a very annoying bug.

---

