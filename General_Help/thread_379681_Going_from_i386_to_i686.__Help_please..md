---
title: "Going from i386 to i686.  Help please."
date: 2007-03-08
forum: General Help
---

### Post by Support the 2nd on 2007-03-08
I installed the i686 linux-image with the Synoptic Package Manager.  But then did the notification update thing and it offered me a ton of i386 stuff.  I unchecked all of those and just installed the other stuff.  Should I go into the Synoptic and install all of the stuff that says i686?  Including "restricted modules" and stuff?  And should I also uninstall the i386 stuff and the same time or afterwards.....I think afterwards because I notice I can boot from 386 via GRUB at the start, and maybe it might save me is the install goes bad for 686.

---

### Post by dexter on 2007-03-08
I thought i686 = i386 + extra gizmo's (like SSE) instructions and stuff. You should not deïnstall all your i386 stuff (i would not recommend it). i386 programs can be run from a i686 kernel.

Did you booted the i686 kernel when the popup button appeared with the i386 stuff ?

What version of Ubuntu are you using ? If it's 6.10 are above, you can install the generic kernel, which selects what your machine is capable of running (in your case that would be i686).

---

### Post by hardyn on 2007-03-08
i don't think there is a 686 package anymore, (somebody may correct me if am wrong) as the 386 will act like a 686 package.

what version are you running?
since edgy the 386 package is a uniprocessor generic kernel

---

### Post by Support the 2nd on 2007-03-08
I am running 6.06.1

I didn't uninstall anything.  I just read on something that i686 was for P2-p4 processors and supports HyperThreading.

But ya, at the boot screen it offers 686 or 386, and I booted off the 686.  I figured it was better because that is what FireFox 2.0 if for.

Should I uninstall the 686 and then boot off the 386 and install the 386 updates?

---

### Post by DagMan on 2007-03-08
I thought it was the generic kernel that was one kernel to rule them all.  It doesn't matter though and I'll keep this really simple: Yes, it is a good idea to keep both kernels in case one gets corrupted or whatnot.  If you only have one kernel and can't boot into it then you have to boot into the live cd and fix it from there.  Also, you don't have any good reason to uninstall the old one unless you need the disk space, so why bother uninstalling it?

Edit: Yeah I think Dapper does have the 386 and 686 kernels and not just the generic.  Also, I forgot to add this but another reason for keeping them both is that chicks dig it.

---

### Post by hardyn on 2007-03-08
as i understand it... 386 and Generic are identical with the exception of SMP...

Which is great, as there is lots of trouble with sony P-M notebooks and the SMP kernel.  something to keep in mind... 

i have also heard reports of (un confirmed) of speed enhancements with with using 386 on uniprocessor machines.

---

### Post by Support the 2nd on 2007-03-08
I installed the updates, but now I have three boot choices plus the three recovery options.

One i686, and two i386.  One of them is 2.6.15-26-386 and the other is 2.6.15-28-386.

This slightly confuses me.  Should I just install of the 686 stuff an just boot that since it is Ubuntu 6.06.1?

---

