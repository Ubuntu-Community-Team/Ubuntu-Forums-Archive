---
title: "Asus Zenbook freezing"
date: 2015-06-23
forum: General Help
---

### Post by Jedwinjim on 2015-06-23
Bonjour, just bought myself an ASUS zenbook UX31E second hand from gumtree. Replaced windows with Ubuntu 14.10 straight away. All works fine out of the box, no complaints. Until my battery power runs out a little (below 60ish%) and it will start to freeze on me. If I'm watching video (either on the hard drive or streaming) it freezes regardless of battery life remaining.

The thing runs flawlessly when plugged into the mains (can watch video endlessly for hours!) with no freezing! So a simpleton like me would assume it's a battery issue, and I can simply buy a new one to eradicate the problem. However (!), can someone with far more technical 'know-how' confirm (or help me run tests to confirm) that this is indeed the solution, before I go out & spend half of what I paid for the laptop on a new battery, if this isn't necessarily what is causing the problem?

Many thanks in advance.

J

---

### Post by TheFu on 2015-06-23
14.10 support ends this month. [http://www.ubuntu.com/info/release-end-of-life](http://www.ubuntu.com/info/release-end-of-life)
Better to move to 15.04, it has support until December (this year) or go with an LTS release - 14.04, 16.04, 18.04 ... so you can plan ahead - each of those LTS releases has 5 yrs of support, not 9 months.

So - I have a chrome book that was locking up after a period of time - couldn't even connect over ssh from another computer on the network - so it was definitely a system issue, not just a GUI issue.  The default size for swap partition was too small.  The chromebook only had 2G of RAM, so 2G of swap was created.  For a desktop, the minimal swap needed thanks to firefox and chrome/chromium browsers is 4G.  For me, I had to massively repartition things since the entire OS was on encrypted storage.

Since changing the swap partition size - zero lockups.  Don't know if that is your issue or not - watch memory use. Nothing will make an OS more upset than running out of memory/virtual memory.

---

