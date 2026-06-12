---
title: "Ubuntu freezing - how to investigate"
date: 2006-10-17
forum: General Help
---

### Post by DavorC on 2006-10-17
I am experiencing occasional system freezes. It happens in X only -- the entire screen goes white and the computer does not respond any more to anything but power-cycle. I had the same issue in Breezy, then switched to Gentoo 2006.0 where everything worked fine, and now that I'm back to Ubuntu with Dapper, I see the issue is still there. It usually happens within an hour, especially once I start up Firefox and/or Thunderbird.

I've had this happen with open-source Radeon driver on Dapper and ATI's fglrx drivers and the generic VESA on Breezy. As I already mentioned, this did not happen on Gentoo (both 2.6.15 and 2.6.16 kernels) nor on Windows XP sp2 (dual-boot).

I filed a bug on Launchpad (#46470), but nobody has answered yet (five months). This is a very serious issue for me, as it prevents me from using my Ubuntu box for any real work. I would be happy to do any further investigation that would help in narrowing down the problem, but am at a loss at where to even start. I've never seen Linux crash so hard with a production kernel, there are no kernel panic messages on the screen that might indicate the source of the problem. I have suspected hardware fault, but I can run memtest for hours with no reported errors, and I drive the machine much harder in Windows XP than I do in Ubuntu and it never crashes. If anyone can advise what to do next, especially how to capture more information when the system crashes, please let me know.

Thanks,

Davor

---

### Post by marianom on 2006-10-17
Try reading var/log/kern.log (for the matter you should check all logs).
Maybe there's a message there that might point in the right direction.

---

### Post by DavorC on 2006-10-17
There is nothing in kernel.log about the crash. There is a log of startup, and then the next startup after I had to reboot the machine. Nothing in between.

---

