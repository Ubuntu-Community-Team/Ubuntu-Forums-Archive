---
title: "[SOLVED] My printer just stopped working! What?!"
date: 2007-10-09
forum: General Help
---

### Post by FuturePilot on 2007-10-09
Out of no where. I can't print anything from my one printer anymore. (HP Laserjet 2420)
If I go to to the printers Properties I see this
```
Ready: open print channel failed; will retry in 30 seconds...
```
And the cups error log is loaded with these
```
E [09/Oct/2007:14:41:45 -0400] cupsdAuthorize: Local authentication certificate not found!
E [09/Oct/2007:14:41:50 -0400] cupsdAuthorize: Local authentication certificate not found!
E [09/Oct/2007:14:41:51 -0400] cupsdAuthorize: Local authentication certificate not found!
E [09/Oct/2007:14:41:51 -0400] CUPS-Add-Modify-Printer: Unauthorized
E [09/Oct/2007:14:46:45 -0400] cupsdAuthorize: Local authentication certificate not found!
E [09/Oct/2007:14:46:45 -0400] cupsdAuthorize: Local authentication certificate not found!
E [09/Oct/2007:14:46:50 -0400] cupsdAuthorize: Local authentication certificate not found!
E [09/Oct/2007:14:46:50 -0400] cupsdAuthorize: Local authentication certificate not found!
E [09/Oct/2007:14:46:50 -0400] cupsdAuthorize: Local authentication certificate not found!
E [09/Oct/2007:14:46:55 -0400] cupsdAuthorize: Local authentication certificate not found!
E [09/Oct/2007:14:46:55 -0400] cupsdAuthorize: Local authentication certificate not found!
E [09/Oct/2007:14:46:55 -0400] cupsdAuthorize: Local authentication certificate not found!
E [09/Oct/2007:14:46:57 -0400] cupsdAuthorize: Local authentication certificate not found!
E [09/Oct/2007:14:47:01 -0400] cupsdAuthorize: Local authentication certificate not found!
E [09/Oct/2007:14:47:03 -0400] cupsdAuthorize: Local authentication certificate not found!
E [09/Oct/2007:14:47:03 -0400] cupsdAuthorize: Local authentication certificate not found!
E [09/Oct/2007:14:47:03 -0400] cupsdAuthorize: Local authentication certificate not found!
E [09/Oct/2007:14:47:08 -0400] [Job 6] No %%BoundingBox: comment in header!
E [09/Oct/2007:14:47:08 -0400] cupsdAuthorize: Local authentication certificate not found!
E [09/Oct/2007:14:47:08 -0400] cupsdAuthorize: Local authentication certificate not found!
E [09/Oct/2007:14:47:08 -0400] cupsdAuthorize: Local authentication certificate not found!
E [09/Oct/2007:14:47:13 -0400] cupsdAuthorize: Local authentication certificate not found!
```
I don't get it. It was working minuets ago!:confused:
But I can still print from a different printer.:confused:
I've purged cups and reinstalled but no go.

---

### Post by FuturePilot on 2007-10-09
Wow. That's what happens when you use HPLIP. I don't get that thing because it doesn't work with 2 of my 3 HP printers.:confused:
So. Removed printer. Rebooted, reinstalled printer this time using the one listed with a USB number next to it (For some reason it wasn't showing up before)
hp LaserJet 2420 (hp LaserJet 2420 USB#2)
All works again.:)

Now why doesn't HPLIP work at all?:confused:

---

