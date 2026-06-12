---
title: "HP Printer - known communication error 5012"
date: 2014-02-25
forum: General Help
---

### Post by gringo.g on 2014-02-25
I have Deskjet F2280. I've installed HP drivers and software. Now, when I turn on my printer while working on the computer, I receive "device communication error 5012" in HP Device Manager. It's a known problem associated with URI address. I found this solution [http://ubuntuforums.org/showthread.php?t=2001912](http://ubuntuforums.org/showthread.php?t=2001912) but how to get the correct address IP for my printer? Is it necessary at all if it doesn't support a wireless port?

---

### Post by tgalati4 on 2014-02-25
Many HP printers can't support both USB connection and ethernet connection at the same time.  So how exactly is the printer connected?

---

### Post by gringo.g on 2014-02-25
By a USB, of course.

Edit:
When I turn off and turn on the printer there are some problems to connect with it. Then I have to go System settings -> Printers -> Server -> Connect and from the list I choose "/var/run/cups/cups.sock", not localhost. After a while the printer is visible.

---

### Post by tgalati4 on 2014-02-25
It's possible your printer is having hardware problems.  Quality control is not the greatest on HP printers and many have flakey processors that cause intermittent behavior.  USB should be plug-and-play.  If you have to reboot your printer often to get it to print, then you have a possible board problem inside the printer and no linux tricks will fix that.

---

