---
title: "What the &lt;bleep&gt; happened?"
date: 2015-10-07
forum: General Help
---

### Post by mbott on 2015-10-07
This morning, I get notified of a software update in 14.04. However after applying the update and rebooting, I cannot sign into my system. Enter my password, get the spinning wheel and Nada. Locks up tighter than a drum after about 8 seconds. A total freeze.  First time I've ever encountered anything like this with Ubuntu.

Looking for suggestions.

-- 
Mike

---

### Post by howefield on 2015-10-07
In the short term, try booting into a previous kernel.

If you don't get a grub screen at boot up, press the shift key after switching the machine on and press the advanced options button and choose the previously working kernel. If that doesn't help then post back.

---

### Post by mbott on 2015-10-07
Thanks!  Well, that gets me in, but I get at least three system errors it feels that it needs to report.  But it's a start.  Will allow me to copy the important stuff off until I can spend some quality time with it.

-- 
Mike

---

### Post by mbott on 2015-10-07
As I mentioned in another thread, today's 14.04 update totally killed my system. Took the opportunity to jump to 15.04 instead of waiting who know how long for a fix.  Not looking back.

-- 
Mike

---

### Post by Michael_McMahon on 2015-10-08
Same thing with me. I hadn't updated in a while so there was lots of stuff, but system (Lenovo T420) was unusable afterwards.
I can confirm that booting the previous kernel (3.13.0-63) works fine for now.

- Michael

---

### Post by Giantmundo on 2015-10-08
I just updated my 15.04 system with a kernel update and same thing.  Spinning wheel with login.  Had to revert to a previous kernel.  Most disturbing.

---

### Post by mbott on 2015-10-08
So, in simple English, can anyone explain exactly what happened with this update? What went wrong?

-- 
Mike

---

### Post by howefield on 2015-10-09
> **mbott said:**
> So, in simple English, can anyone explain exactly what happened with this update? What went wrong?

A buggy kernel was uploaded to -proposed, a repository not enabled by default so only those willing and able, with a higher tolerance to breakage would/should be affected.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1503655](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1503655)

---

### Post by mbott on 2015-10-09
> **howefield said:**
> A buggy kernel was uploaded to -proposed, a repository not enabled by default so only those willing and able, with a higher tolerance to breakage would/should be affected.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1503655](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1503655)

OK, well I've turned off -proposed after I reloaded an image of 14.04 made just about a week prior to this incident.  Living on the edge can give you a nose bleed.  Thanks for the simple explanation.

-- 
Mike

---

### Post by Michael_McMahon on 2015-10-09
> **howefield said:**
> A buggy kernel was uploaded to -proposed, a repository not enabled by default so only those willing and able, with a higher tolerance to breakage would/should be affected.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1503655](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1503655)
Thanks for the information! I'd like to disable -proposed also, but is it better to wait for a fixed kernel in that repository and then disable it? 
Or is it possible to disable now, and remove some set of packages related to the buggy kernel?

- Michael

---

### Post by howefield on 2015-10-09
> **Michael_McMahon said:**
> Thanks for the information! I'd like to disable -proposed also, but is it better to wait for a fixed kernel in that repository and then disable it? 

It's your choice really, chances are the new package is already waiting for you in -proposed.

> Or is it possible to disable now, and remove some set of packages related to the buggy kernel?

Yes, it's possible.. use something like

```
sudo apt-get purge linux-image-x.x.x-xx-generic
```

and replacing x with the actual version numbers to remove the offending kernel and disable -proposed. I'd just hold off and wait for the new package given that if it isn't already there, it will be very soon. :)

---

### Post by Michael_McMahon on 2015-10-09
> **howefield said:**
> It's your choice really, chances are the new package is already waiting for you in -proposed.

You're right. I just updated and the latest version seems to work. Thanks!

---

### Post by howefield on 2015-10-09
Terrific, thanks for the update. :)

---

