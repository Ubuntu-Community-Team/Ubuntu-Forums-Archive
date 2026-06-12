---
title: "Chromium-browser won't start, Ubuntu 16.04.3"
date: 2017-10-19
forum: General Help
---

### Post by t0p on 2017-10-19
At long last I've put Ubuntu 16.04.3 on one of by boxen.  But immediately hit on a problem.  I use Chromium (aka "Chromium-browser") on my computers, and I've apparently managed to install it on my dual-boot laptop.  Its icon appears on the left-side of the monitor, but clicking it takes me nowhere.

I really don't want to have to mess about installing a different browser on my machines (yes, Firefox is nice, but I have everything working grrreat with Chromium (apart from this slip-up).  Please can someone tell me whatever it is I'm missing to have Chromium working nice like it does on my other machines.

Help?  I hope so.  Cheers!

---

### Post by TheFu on 2017-10-22
To troubleshoot, open a terminal and run the browser from that window. Any warnings or errors should be displayed in the terminal so you can hunt them down for solutions.

Another technique is to create a new userid, login to that other ID and try again.  This will determine if the problem is with a single userid or with the entire system.  It is useful to remember that Linux is multi-user, always.

---

### Post by missmoondog on 2017-10-22
i see your distro says version 12.04. how old is your machine? does it support sse2? if not, very browsers will work on it except palemoon nonsse.

[https://forum.palemoon.org/viewtopic.php?f=40&t=13530](https://forum.palemoon.org/viewtopic.php?f=40&t=13530)

just taking a stab in the dark with the limited info you provided

---

