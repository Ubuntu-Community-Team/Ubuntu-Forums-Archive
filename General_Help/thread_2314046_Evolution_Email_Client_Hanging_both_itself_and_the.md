---
title: "Evolution Email Client Hanging both itself and the whole desktop."
date: 2016-02-18
forum: General Help
---

### Post by neltnerb on 2016-02-18
I'm not quite sure how to report this as a bug since the behavior is varied, but searching the archives shows lots of sort of similar but not quite the same problems.

For several years now, when I do things like move email messages or move images in HTML email I am composing, it hangs evolution (at least) and often the whole desktop environment. Started with perhaps Ubuntu 12.10? Definitely still here on my current computer running 15.04.

I'm running on a Core i7-5557U with 16GB of RAM and don't even have a swap partition, so I'm not running out of memory. But the CPU is always pegged when this happens. The icon changes to the drag icon, and just doesn't turn back or let me click anything anywhere on the desktop until either I wait it out or go to a VTTY and kill evolution.

It started happening with the implementation of the new Unity environment, so my best guess is that dragging things is sending some meta-information to the desktop environment (which makes sense for use in dragging things to the desktop or side bar), but it's doing it insanely poorly and blocking the UI perhaps? I can't even click icons in the side bar when it's like this, so it seems to extend outside of Evolution alone.

Does no one else using evolution have this issue? It's persisted between two different computers now, so I feel like someone else must be seeing this insanity. I really love Evolution otherwise (been dealing with this bug for years and still using it, so...) since it lets me have multiple email accounts, works with exchange, and does the integrated calendar, but this is driving me nuts slowly.

---

