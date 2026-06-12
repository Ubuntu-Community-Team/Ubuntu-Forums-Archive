---
title: "hangs at shutdown"
date: 2015-04-13
forum: General Help
---

### Post by Prem_Reginald on 2015-04-13
Hi, 

My Ubuntu happens to hang at shutdown. Here is an image of the problem I face.

Initially it hanged at "applying power safe settings". Now for some reason, it is able to get past that and hangs at "kvm: exiting hardware virtualization".

How can I overcome this issue?

Thanks.

---

### Post by Prem_Reginald on 2015-04-15
bump

---

### Post by sotramk on 2015-05-07
having the same problem.
shutting down from the terminal works

shutdown -P now

---

### Post by mattharris4 on 2015-05-07
I don't know what causes this but with an old Windows XP computer (Linux was not installed on this computer) it would hang up and not complete power-down requiring a hard power-off.  It took wiping and reinstalling Windows to rectify the issue.  As a last resort maybe that would work for your Linux install.  Back up all of your documents, pictures, videos, etc. before doing this.  If you have a dual-boot install you will likely have to wipe the whole drive and reinstall both OSes (usually a version of Windows and the Canonical OS you installed).  There are theoretically ways to keep Windows and wipe/reinstall Linux but many times doing this will bork the Windows install anyway.

Before wiping and reinstalling, what version do you have?  If it isn't 14.04 LTS (and is newer, say 14.10 or 15.04) and you have a computer that is a year old or older try the LTS version.  The non LTS versions are really meant for developers and programmers to test, some very new computers require those versions but non-LTS versions are going to be buggy due to them mainly being for testing and repairing new features for the next LTS version (16.04 due in April 2016).  Take a look at the first month of bug reports for 15.04 (that is all there is at the time I posted this), then look at the first month of bug reports for 14.04 LTS and you will see what I mean.

---

