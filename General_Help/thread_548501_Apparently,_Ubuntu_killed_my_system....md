---
title: "Apparently, Ubuntu killed my system..."
date: 2007-09-11
forum: General Help
---

### Post by morgond on 2007-09-11
I have a dual-boot system on my laptop with Ubuntu Studio 7.04 and WinXP SP2.  I use WinXP the majority of the time, using Ubuntu mainly to familiarize myself with Linux and ubuntu.

I installed Ubuntu by using the Wubi installer for Windows. It's worked just fine for the past few months.

this morning, I booted up Ubuntu, and while resizing a window, the system froze up. I had desktop effects enabled, and I've had a couple of problems with them enabled before, so I'm assuming that's what triggered the freeze.  After waiting a few minutes, I manually reset the computer and booted up again, to be met with the message that the hal.dll file was missing.

I can no longer boot up my computer.

I got into it by putting in the Ubuntu 7.04 live CD, and was able to back up my documents.  But I found that the system was only able to read part of the hard drive. On the main disk (C:) the first few directories are there (including Documents and Settings, thank God), but there is no longer any Program Files directory or Windows directory.

I did some searching around to find out if I could fix the missing hal.dll file problem. Most of the fixes require you to be able to boot into the recovery console (safe mode with console), but, though I can bring up the boot options menu, I can't use any of the options without getting the same hal.dll missing error.

So, now I'm in a quandry. I'm missing a WinXP disk, apparently, and I'm pretty ticked off at Ubuntu right now. If there was the chance that the desktop effects could wipe out part of your hard drive, why in the world were they included as an option in the main interface?

Any help for this problem, or do I just have to re-install an OS?

---

### Post by reckless2k2 on 2007-09-11
i don't have a simple answer for your problem but we are talking about use at your own risk software. even windows recommends that you backup.

---

### Post by p_quarles on 2007-09-11
Desktop effects didn't do anything to your hard drive. It's in development, but it's certainly not *that* volatile.

Anyway, the most likely problem here is that you opted to use Wubi instead of following the straightforward and easy dual-boot installation instructions provided by Canonical. I know that some people think this installer is more convenient. However, you can't be "ticked off at Ubuntu" when you didn't even follow the directions. 

It sounds like Wubi borked your XP installation, and I have no idea how you would fix that without some kind of recovery disk for Windows.

---

### Post by FuturePilot on 2007-09-11
I did some searching and this *is* fixable, but you need an XP CD. Do you know anyone you could borrow one from just to fix this? 
[http://www.computerhope.com/issues/ch000490.htm]("http://www.computerhope.com/issues/ch000490.htm")
This has nothing to do with the desktop effects though. It has to do with the fact that when you use Wubi it install Ubuntu inside your Windows partition. On a normal install this would never happen. Wubi is currently an unsupported install method.

---

### Post by southernman on 2007-09-11
Sounds like a simple case of PEBKAC

None the less, even though you blame Ubuntu (entirely NOT the OS fault)...

[Go here]("http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm") or [here]("http://www.google.com/search?q=hal.dll&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a") to see if you can find a solution to your problem.

Good Luck..

---

### Post by morgond on 2007-09-11
I'm not really ticked...

I have had everything backed up, so it wasn't that big of a deal, more of just an inconvenience of having to reinstall.  I'm reinstalling Ubuntu, in case you're wondering, and this is from the official CD.

I'm new to dual-booting, so I did take precautions. My WinXP cd apparently was 'borrowed' recently. :P

Didn't think of it being because of Wubi, but I've duly noted that for future reference and warning. Thanks.

---

### Post by reckless2k2 on 2007-09-11
> I'm not really ticked...

> and I'm pretty ticked off at Ubuntu right now

hahaha...what is this then? hahahaha...or is "ticked" just a way of saying everything is cool in the pool. hahaha. now if you said "ticked ticked" now that would've meant gloves off and someone hold your watch...hahahaha

---

### Post by dabl on 2007-09-11
> **morgond said:**
> 

After waiting a few minutes, I manually reset the computer and booted up again



In addition to the other wise advice provided above, it is not necessary (and may be counter-productive) to use the "kill" switch on your Linux system -- here is the better way:

[http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

:)

---

