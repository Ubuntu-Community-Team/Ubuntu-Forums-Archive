---
title: "Power problems with new kernel"
date: 2013-05-03
forum: General Help
---

### Post by montag dp on 2013-05-03
Hi, I recently installed Ubuntu 13.04 on my Thinkpad T430 (Ubuntu Gnome, actually, but the DE is immaterial).  It was a clean install, wiping my old one.  Shortly after installing, the updater recommended system upgrades.  One of the things installed was a kernel update, 3.8.0-19-generic.  I don't remember which kernel was there before, but the original one didn't have any of the problems I'm about to mention.

The first thing I noticed with the new kernel was that power usage was up.  At idle, it consumed 1 - 2 more watts, which on my machine is about a 15 - 30% increase.  The CPU temperature at idle was also up by 5 - 10 degrees, and the fan was running constantly.  Additionally, I couldn't get hibernate to work.

I ended up installing the kernel that worked well on Quantal, 3.5.0-28-generic.  This has solved all these problems.  Power usage, CPU temperature, and fan usage are all back down to what I was seeing before the upgrade.

So I guess I have a couple questions.  First, is anyone else having similar problems?  Second, should I report this as a bug, and, if so, where?  I'm not sure if the problem is specific only to my hardware, but Thinkpads are supposed to be well supported.  I also don't know what I would report, because I don't know specifically what is causing the problems.  However, I don't want to have to be stuck on an older kernel for all of eternity if this isn't fixed.

---

### Post by ferd on 2013-05-03
Same with me but am running a hp pavilion m6. I was very happy with the temp decreases with the kernel with the original install of raring but the newer kernel has the temps back to the 3.5.0-28 higher levels. Not quite the same problem, but similar.

---

### Post by montag dp on 2013-05-03
> **ferd said:**
> Same with me but am running a hp pavilion m6. I was very happy with the temp decreases with the kernel with the original install of raring but the newer kernel has the temps back to the 3.5.0-28 higher levels. Not quite the same problem, but similar.Yeah, seems like a slightly different problem, because the kernel I went back to is actually 3.5.0-28, which works fine for me.

Is it just me or does it seem like new kernels are coming out at a ridiculously fast pace the last year?  I'd prefer them to come out less frequently and do more testing to make sure there aren't regressions like this.

---

### Post by ferd on 2013-05-03
Linus and his crew seem to be working overtime. We can only hope that items affecting us are not beling missed because of the release schedule. Also, have you tried tlp for temperature management. It has made a notable lowering of my four cpu temps.

---

### Post by montag dp on 2013-05-03
> **ferd said:**
> Linus and his crew seem to be working overtime. We can only hope that items affecting us are not beling missed because of the release schedule. Also, have you tried tlp for temperature management. It has made a notable lowering of my four cpu temps.Yes, I have been using that since Jupiter went away.  The problems I mentioned were with TLP running.  It probably would have been worse without it.

---

### Post by montag dp on 2013-05-16
There was a new update to Ubuntu base today which installed kernel 3.8.0-21-generic.  The power problems appear to be fixed (for me) on this newer kernel, FYI.

---

### Post by ferd on 2013-05-16
> **montag dp said:**
> There was a new update to Ubuntu base today which installed kernel 3.8.0-21-generic.  The power problems appear to be fixed (for me) on this newer kernel, FYI.
Unfortunately, it has had the opposite effect for me. The temperature increase in about twenty five degrees fahrenheit.

---

### Post by montag dp on 2013-05-26
> **ferd said:**
> Unfortunately, it has had the opposite effect for me. The temperature increase in about twenty five degrees fahrenheit.That's too bad.  There was another update recently to 3.8.0-22 and unfortunately the power problems seem to be back, so I removed it and went back to 3.8.0-21 for now.  It's kind of annoying how these things happen.

---

### Post by hansdown on 2013-05-26
Hi montag dp.

If you do choose to file a bug report, the DE, and graphics hardware "is" important.

Thanks.

---

### Post by wildmanne39 on 2013-05-26
The 3.8 kernel also has the same heating issue with my gateway.

I am currnetly booting the older 3.5 kernel.

---

### Post by montag dp on 2013-05-27
> **hansdown said:**
> Hi montag dp.

If you do choose to file a bug report, the DE, and graphics hardware "is" important.

Thanks.Thanks.  I will file one when I get time.

It's rather strange that for me, 3.8.0-21 actually works better than the older 3.5 kernel, reaching lower minimum watts, but 3.8.0-19 and 3.8.0-22 are much worse.  I wonder why the problem would have been fixed and then later broken again?

---

### Post by Linuxisfast on 2013-05-27
I have run both 12.04 with 3.5 kernel as well as the 13.04 with latest kernel 3.8 series. What I observe, compared to Unity, KDE takes far less CPU load in Raring and thereby on average compared to Unity in 12.04 and 13.04, it runs much cooler.

---

### Post by montag dp on 2013-05-27
> **Linuxisfast said:**
> I have run both 12.04 with 3.5 kernel as well as the 13.04 with latest kernel 3.8 series. What I observe, compared to Unity, KDE takes far less CPU load in Raring and thereby on average compared to Unity in 12.04 and 13.04, it runs much cooler.For me, KDE on the 3.5 kernel used the same power as Gnome Shell on 3.5 or 3.8.0-21.  I haven't tried Unity, though, or KDE on 3.8.

---

### Post by montag dp on 2013-08-07
Another FWIW, but 3.8.0-27 is working fine for me.  Actually the temperature and power consumption are a little better than on 3.8.0-21.

---

