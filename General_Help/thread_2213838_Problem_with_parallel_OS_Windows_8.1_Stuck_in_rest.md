---
title: "Problem with parallel OS Windows 8.1: Stuck in restart loop after updates"
date: 2014-03-28
forum: General Help
---

### Post by Rob_Weister on 2014-03-28
Hi all,

I'm reltively new to Ubuntu and have been running it parallel to Windows 8.1, and everything was going more or less fine until last night when a very annoying issue occured.  Windows did its automatic update, but it was apparently a big one and needed to restart after booting.  The damn thing won't apply the updates after the reboot though, and is now stuck in a restart loop.  The first thing I thought of was that maybe the grub is somehow interrupting the update installation process, given that I have to select Windows 8 manually instead of it booting by default.  Had anyone else run across this issue?

---

### Post by GigabyteProduction on 2014-03-28
the windows bootloader is chained from grub, so it won't be grub since grub basically shuts off and starts the windows bootloader, to the windows bootloader, it's like nothing happened. so it has to be an issue in windows, or maybe it's just a lot of updates, have you ever noticed that when you make windows check for updates, it only gets so many? after you install all of them, it suddenly detects 50 more... so check and see if it's different updates and if it is, just let it get through all of them.

---

### Post by Rob_Weister on 2014-03-29
>  have you ever noticed that when you make windows check for updates, it  only gets so many? after you install all of them, it suddenly detects 50  more... so check and see if it's different updates and if it is, just  let it get through all of them. 				

Huh... well it seems you were correct, Gigabyte.  Two more reboots were enough to finish the process.

Regardless, I still think it's pretty excessive to require literally 6 restarts just to apply a week's worth of updates.  Probably so they could install all of the NSA's data mining bots and backdoors.  Lol stupid Microsoft...

---

### Post by GigabyteProduction on 2014-03-29
Well i'm glad i could help. I am helping excessively. i subscribed to the entire forum with rss so i can see every new topic started, but it's i'm looking at this like non-stop. I didn't expect this many topics to be started. I just finished all of my unread feeds but after 30 seconds of watching good mythical morning thunderbird updated and found 10 more.

---

