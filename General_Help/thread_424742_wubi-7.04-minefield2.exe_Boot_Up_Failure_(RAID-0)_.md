---
title: "wubi-7.04-minefield2.exe Boot Up Failure (RAID-0) #2"
date: 2007-04-27
forum: General Help
---

### Post by Dark Legacy on 2007-04-27
Wubi Version: wubi-7.04-minefield2.exe
Diagnosis: Boot up Failure.
Data:

[img]http://img249.imageshack.us/img249/8038/wubimediumsw7.jpg[/img]

It's pretty much the same error listing as the last version of Wubi, and the creator has promised to include RAID-0 support in this build.

I really want to use Ubuntu on my machine. :(

---

### Post by tuxcantfly on 2007-04-27
> It's pretty much the same error listing as the last version of Wubi, and the creator has promised to include RAID-0 support in this build.

I assume you're talking about ago's mention of adding support for raid  in the newer source tree. It's already been added, only we need to tweak out the additional bugs and flaws in that source tree until we can release a working build

I built this build, not ago; it was simply a temporary build with a fix to allow using the final feisty release version; it is otherwise exactly the same as beta-v3; no raid support here, yet... we'll have it done as soon as we have the new source tree in a working state

We'll probably have it working in a few weeks, just wait...

---

### Post by Dark Legacy on 2007-04-27
> **tuxcantfly said:**
> I assume you're talking about ago's mention of adding support for raid  in the newer source tree. It's already been added, only we need to tweak out the additional bugs and flaws in that source tree until we can release a working build

I built this build, not ago; it was simply a temporary build with a fix to allow using the final feisty release version; it is otherwise exactly the same as beta-v3; no raid support here, yet... we'll have it done as soon as we have the new source tree in a working state

We'll probably have it working in a few weeks, just wait...

Thank you for your commitment and support. I don't mind waiting a few weeks. :)

---

### Post by AidanPM on 2007-05-14
I got the Exact same message twice, the first time I thought I screwed something up in windows. But the second time it happened the only thing I did differently before it gave me this message was a hard reset(cut the power to my box) of my computer. And the more I thought about it, I realized that that was the only thing the two incidences has in common.

the first time I didn't know what to do and I figured I didn't have too much to lose so I just reinstalled. But this time I have everything customized to the MAX and I don't want to lose anything. So is there anything I can do to make it go back to normal, without reinstalling?

---

### Post by bnovc on 2007-08-23
It looks like this still hasn't been implemented on the download from August 23rd, 2007.

---

### Post by tuxcantfly on 2007-08-24
> It looks like this still hasn't been implemented on the download from August 23rd, 2007.

Well some raid support was implemented, using dmraid, but it seems like your particular hardware config isn't supported, maybe try disabling raid temporarily for installation (install to a small non-raid partition) then you can try to configure your raid chipset afterwards, once it's installed.

---

