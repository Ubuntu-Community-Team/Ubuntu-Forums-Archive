---
title: "Uninstallation Help!"
date: 2008-07-03
forum: General Help
---

### Post by pawantahiliani on 2008-07-03
Okay, I installed ubuntu yesterday..and I want to remove it until I can calm my nerves after 5 hours of error 17!

Now, these are my basic computer specs

It is an hp dv9000 (17 inch, hd dvd drive)
I have two 120gb SEPARATE SATA DISKS...c:\ and d:\

Windows is installed in c:\
Ubuntu in d:\...whole drive used for ubuntu

I DO NOT HAVE AN XP CD and only recovery disks!

Now, If i remove ubuntu from d:\..i get error 17 because apparently the GRUB file is still present and is affecting my MBR!

I checked online and I found that the xp cd has a fixmbr option in the recovery console..

problem is..when i use an xp cd it says no drives plugged it or detected! and I havent tried my hp recovery disks yet..

Can someone help me clear ubuntu from my pc and fix it back to normal with these conditions?:S

---

### Post by justleen on 2008-07-03
you;d have to restore the windows MBR.

this can normally done with the XP cd, by entering rescue mode... I dont know if your recovery Cd's contain a resue-shell.

if it does have a rescue mode, its sufficient to run "fixboot" and "fixmbr" from the rescue console.

If it doenst, download supergrub and install it on a usb stick (supergrub can restore windows MBR...)

---

