---
title: "Silent reversal of apt-mark hold"
date: 2020-05-24
forum: General Help
---

### Post by &amp;KyT$0P# on 2020-05-24
I had used [FONT=Courier New]apt-mark hold[/FONT] on packages that are not installed, as a means to block them from ever being installed.  I just discovered that on two different 18.04 machines, my holds were silently cancelled.  [FONT=Courier New]apt-mark showhold[/FONT] doesn't return anything.

As a test, I tried:

1) reinstate the hold

2) [FONT=Courier New]sudo apt-get update[/FONT]

3) Check that the hold was still there.  It was.

4) [FONT=Courier New]sudo apt-get dist-upgrade[/FONT] (this only upgraded a few packages that are held back because phased updates)

5) Check again if the hold exists...nope, it's now gone again?

Why is the hold disappearing?
How to stop it?
If it can't be stopped, how to properly blacklist packages from ever being installed?  That is, tell apt that installing something that Recommends or Suggests [COLOR="#FF0000"]<package>[/COLOR] should skip that recommendation/suggestion, and trying to install something that Depends on [COLOR="#FF0000"]<package>[/COLOR] should just refuse with an error.  I rather not rely entirely on me noticing and manually aborting.

---

### Post by &amp;KyT$0P# on 2020-05-26
bump.

I see this behavior in 20.04 also.

---

### Post by &amp;KyT$0P# on 2020-06-03
bump

---

### Post by &amp;KyT$0P# on 2020-06-10
bump

---

### Post by norobro on 2020-06-10
Looks like that is the intended behavior, but it is on the wishlist ;) [https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1694989](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1694989)

You might try 'Pinning'. I have run Debian systems for years and have pinned installed packages but have never tried to pin a package that isn't installed. [https://help.ubuntu.com/community/PinningHowto](https://help.ubuntu.com/community/PinningHowto)

That link is to an Ubuntu wiki so I'm not sure what this means: > Note however that the processes described below will only work if things like libc6 versions match, so you should probably not do this on an Ubuntu system.HTH

---

### Post by &amp;KyT$0P# on 2020-06-11
Thanks norobro, pinning works! :KS

> **norobro said:**
> That link is to an Ubuntu wiki so I'm not sure what this means:

It's referring to this -
> allows you to remain on a stable release of Ubuntu (or any other debian system) while grabbing packages from a more recent version. 

Since I'm not mixing binary packages from different distros or OS versions, that doesn't apply here.

---

