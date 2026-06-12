---
title: "Dual booting: Ubuntu flawless, Windows only boots 1 in 3 times"
date: 2008-01-29
forum: General Help
---

### Post by lucasl on 2008-01-29
I have an extremely strange problem. On my computer (with grub), Ubuntu boots perfectly, but Windows only boots 1 in 3 times. The strange part is, it will always boot the third time, but not the first or second. On those, it finishes the windows loading screen with the blue bar, then shuts down. Booting into safe mode works every time.

Background: Brand new computer, installed XP SP2 and then ubuntu 7.10 (alternate).

I doubt it's a hardware error, since its a new computer and it always works the third time, but I can't imagine a software error for the same reasons.

I know it has more to do with Windows than Ubuntu, but I thought maybe this had happened to someone else.

Thanks!

---

### Post by DrMega on 2008-01-29
I've seen this on a number of machines with XP SP2, none of which had Ubuntu (or any other OS) on at the time.

Windows keeps an event log which you can access via Computer Management (right click on my computer, choose Manage, then choose event viewer). Have a look in there and it should give you the last thing it did before it failed, and with a bit of luck, the event that killed it during boot.

If it always boots OK in safe mode, it is most likely a driver conflict. That being the case you might (only might) be able to see what's up if you go into Device Manager and look for any big yellow exclamation marks.

One other unlikely possibility, based on a freinds experience, is a weak power supply. My freind had this problem, put a new PSU in and it was OK. His was more intermittent though, and like you say as there is such a rigid pattern in your case it is unlikely to be hardware related.

---

