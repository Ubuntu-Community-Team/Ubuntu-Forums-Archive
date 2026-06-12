---
title: "Ubuntu 23.04, Logitech G604 scrolling problems"
date: 2023-05-03
forum: General Help
---

### Post by BloodyIron on 2023-05-03
I just upgraded my installation from LTS 22.04 to 23.04, and I'm now having really horrible scrolling problems with my mouse.

I'm using a Logitech G604, with the unified receiver (not bluetooth). Which was working completely reliably with 22.04.

I didn't stop to test much of anything with 22.10, as I was in a time-limited window to upgrade to 23.04. And from what I'm reading online, this issue appears to be specific to Linux kernel 6.1 / onwards.

The issue is two-fold.

1. Out of the box the scroll inputs are barely detected. In free-scroll mode (a feature of a lot of Logitech mice, including this one) it helps, but a lot of the scrolling inputs are still missed. It is effectively completely unreliable to impossible to actually scroll down or up by just one increment. You either scroll too much, or not at all.
2. If I use the Solaar application to toggle "Scroll Wheel Resolution" this now makes scrolling "too fast" in some scenarios, such as with Vivaldi (scrolling through tabs).

I've tried adding  "blacklist hid_logitech_hidpp" to /etc/modprobe.d/blacklist.conf and rebooting, but that did not seem to improve the situation.

What exactly can I do to get my scroll wheel working accurately and reliably again? This is a huge UX problem as I use my scroll wheel in almost every app I use on my computer. Be it gaming, browsing, going through files, CLI stuff, whatever.

Current running kernel: 6.2.0-20-generic #20-Ubuntu SMP PREEMPT_DYNAMIC

---

### Post by launchpad-groovix on 2023-05-09
I just got a G604 and am using 22.04 xfce, 5.15 kernel, and the scroll button only registers randomly if you go slow, maybe 1/3 of the time the scroll movement actually scrolls the web browser.  I've used several other logitech mice and never had a problem like this.  I tried it briefly on a windows system and it didn't seem to have the same problem.   

xev shows every down scroll or up movement so I'm pretty sure it's a software thing.  

Actually I just unplugged my g300s wired mouse that I also had plugged into the same system and now scrolling seems to work reliably!    Then I plugged the g300s back in and scrolling is still fine.   I'll report back if the scrolling problem comes back.

---

