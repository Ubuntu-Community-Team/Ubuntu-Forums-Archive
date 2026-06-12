---
title: "No help anywhere! Black screen after lid open."
date: 2018-07-15
forum: General Help
---

### Post by princesschevy on 2018-07-15
I realize there are several help topics for this issue; however, none of them quite exactly mirror my experience. The help I've researched is either obsolete, irrelevant or just plain wrong. I have tried MANY fixes to no avail. Here's the sitch:

Ubuntu 18.04
Lenovo Z585 with AMD Radeon 7660 
Initial kernel 4.15.7 resulted in great functionality with the exception of the following..

Upon laptop lid closure, the system does effectively enter hibernation. The fans stop, lights off, etc. When you reopen the lid, fans return, lights, but only a glowing black screen. The commonly suggested CTRL+ALT+F1 & F7 keyboard commands are ineffective. 

Screen returns fine from the default 5min blank screen timeout however. Without issue. Only upon return from hibernation or when the lid is reopened. 

Per recommendations, I have installed MANY different kernel versions, all with the exact same result. Some versions even prevented hibernation altogether upon lid closure, but the screen would still go off.. never to return until reboot.

I have tried MANY different recommended actions, checked for AMD drivers for my specific graphics card, to find drivers for a very outdated Ubuntu version. Followed guides for LMT configurations, installing this, manually removing that, replacing this with that, to end up with the same blank screen that either won't enter hibernation, have no WIFI, a jittery screen display, or a scrolling startup screen of failures. At that point I reformatted and reinstalled the whole thing. Back to fresh 18.04 with 4.15.7 kernel. Hibernation is again intact, but still the same black screen on resume.

Im definitely no Ubuntu expert, but I'm hopeful to make the switch to Ubuntu only. I seem to think I'll end up back at Windows with all these [SOLVED] help docs that only end up turning hiccups into heartattacks.

Much appreciation and warm regards in advance.

K

---

### Post by HermanAB on 2018-07-15
Howdy,

A black screen is one of the most difficult things to fix, since you cannot see what the heck is going on.  I have only had a similar issue once before, about 10 years ago, so it does happen to a few unlucky souls, but it is not common.  The root of the problem is that you  need a better display device driver for your laptop device.

The way I would fix it, is to reboot and enable sshd, a remote management system.  Then, when the machine gets into that state, log into the machine over ethernet from another machine to see what is going on. However, this is not for  the faint hearted, or for a beginner.

Deep underneath all Linux distributions are the same.  The differences are mostly in the desktop and display management.  Therefore, my recommendation is that you install a completely different Linux distribution.  By completely different I mean NOT Debian, Mint, Cinamon etc, since they are all related.  Rather try Arch, Fedora, Gentoo or PCLinuxOS.  Chances are that one of them will work properly on your machine.

When all else fails, there are also OpenBSD and FreeBSD!

---

### Post by Yellow Pasque on 2018-07-16
So you have it set to hibernate when you close the lid? If so, have you tried suspend instead? Quick google shows complaints about hibernate on this model.

> The root of the problem is that you need a better display device driver for your laptop device.
The default open source radeon driver is the only one available for the 7660 (not counting generic, unaccelerated drivers). The ancient fglrx/Catalyst driver doesn't work on modern versions of Linux/Ubuntu.
But in that vein, it might be interesting to boot with 'nomodeset' and see if the issue still occurs.

---

### Post by anspectrum on 2018-07-16
I've experienced similar kind of behavior on HP Elitebook Folio 9480 with Ubuntu 16.04 (64-bit). Although  nature of problem is a bit different and random. Some times when I let my laptop stay idle and it goes to screen lock mode (say after 5 mins of inactivity) and then I try to unlock it, there is no password input screen. I can see that Laptop is fully working (like CAPS key is working) but the password screen is not there. Entering password blindly does not help either nor does CTRL+ALT+Fx. But a workaround for me is that I simply close the lid forcing laptop to go into suspend state and then open lid again and viola the password screen comes back and I can successfully log in.

I've also tried to diagnose why does it happen (blank screen) but could not find the exact cause / solution. May be my experience / method could be of some help to you.

---

### Post by dragonfly41 on 2018-07-16
I don't use a laptop today but I remember toggling between (Dell) black screen and working desktop
by hitting Super Key + P Key together.
The Super Key is the one showing windows logo (usually bottom left of keyboard).
I don't know if this works for you and it may be a red herring.

---

