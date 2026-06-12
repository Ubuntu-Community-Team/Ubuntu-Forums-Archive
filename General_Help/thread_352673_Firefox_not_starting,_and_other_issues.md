---
title: "Firefox not starting, and other issues"
date: 2007-02-03
forum: General Help
---

### Post by Zeikcied on 2007-02-03
I'm running Kubuntu (Edgy), and I haven't had any trouble lately.  But for some reason, Firefox won't start all of a sudden.

I don't know what I did.

Another problem is that, when playing Unreal Tournament 2004, every few seconds, the framerate dips.  It didn't do that before.

The only thing I could think of is, I edited xorg.config to remove a "Plug-and-Play Monitor" setting, which I didn't think was necessary.  I had my monitor (or a close enough replacement) already configured, and this PnP Monitor thing was just showing up as a secondary monitor.

Of course, when I rebooted I found that something had pointed to the "monitor1" identifier, which the PnP Monitor had, so I had to reset that.

With UT2004, I tried turning all graphics settings to the lowest, and it still had framerate issues.  And now I find that Firefox isn't starting.  I mean, it just won't start at all.  I try to start it via the Konsole, and it gives me some error about a bad input device on line 169, and then a segmentation fault.

I don't know what to do.  I'm thinking about just reinstalling Edgy, but I don't want to lose my settings (like my high scores in Klickety, or my Wine stuff).  Can someone help?

---

### Post by dexter on 2007-02-03
If your only problem is starting Firefox, you could try reinstalling it. Get it from [www.firefox.com](www.firefox.com), download the linux package, put it say in /opt/firefox and start it by going to that directory and type firefox. If that works, you can redirect the firefox button in the Applications menu to the new directory.

---

### Post by Zeikcied on 2007-02-03
> **dexter said:**
> If your only problem is starting Firefox, you could try reinstalling it. Get it from [www.firefox.com](www.firefox.com), download the linux package, put it say in /opt/firefox and start it by going to that directory and type firefox. If that works, you can redirect the firefox button in the Applications menu to the new directory.
I reinstalled it using Adept, but it didn't work.  At least not right away.

For some reason, after I posted this, and started downloading the Kubuntu Edgy CD ISO file (and leaving the computer for about fifteen minutes), everything started working perfectly again.  Firefox started, and UT2004 had no more framerate lag.

I have no idea what was wrong or why or how it was fixed.  I'm stumped.  I'm just glad it is working now.

---

