---
title: "Windows Mobile 6 &amp; Ubuntu Hardy"
date: 2008-06-01
forum: General Help
---

### Post by WolfyAU82 on 2008-06-01
It's been a few days of Trial'N'Error (the first two days) since I gave Ubuntu a go, but since then I have really covered some ground with basic navigation around the OS (but I've yet to learn how to really get into tinkering with "Under the Hood" as I able to with Windows XP).  I gotta say Ubuntu ROCKS! :guitar:

After messing around with Wine, I am now looking to synchronize my PDA, but since ActiveSync 4.5 isn't compatible with Wine.

How do I sync a HTC 3600i (powered by _Windows Mobile 6_) in Ubuntu Hardy? :-k

---

### Post by mastermatt63 on 2008-06-08
hey man im having the same problems. please let me know if you have any progress. Thx!

---

### Post by odoketa on 2008-06-08
Howdy!

I've been trying for the last hour or so to figure out the easiest way to get my WinMobile 6 phone working. It seems like syncing email is a pretty trivial operation - see for example [here]("http://www.ubuntugeek.com/pocket-pc-syncing-with-evolution-in-ubuntu.html").

Mounting the phone as a drive, which is a much more interesting task, seems to be described [here]("http://ubuntuforums.org/showthread.php?t=444387").

Disclaimer - I haven't tried these yet.

I noted over [here]("http://blogs.msdn.com/jasonlan/archive/2007/03/13/what-file-system-does-windows-mobile-use.aspx") that the filesystem on the phones seems to be TFAT, which according to [msdn]("http://msdn.microsoft.com/en-us/library/aa915463.aspx") is a slightly more stable FAT. I don't know why you can't just mount it as FAT (FS stuff is mostly beyond me) but I haven't seen anyone having luck with that.

Now, to the community at large, winmo seems to be pretty well established - what would we need to do to make it plug-and-play?

---

### Post by mavicdog on 2008-06-08
[This]("http://ubuntuforums.org/showthread.php?t=540330") link says all you need to know. I sync wm6 device through lightning to gmail and the calendar app to gcal with one of the many apps that syncs to google. thunderbird and lightning on the laptop, google on the web and wm6 mobile. the only thing is contact syncing is not there yet (that I know of).

---

