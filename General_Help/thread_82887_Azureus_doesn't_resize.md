---
title: "Azureus doesn't resize"
date: 2005-10-27
forum: General Help
---

### Post by PriceChild on 2005-10-27
Built myself the 1.5 of Java btw, but Azureus still doesn't resize.

The inside bit just stays the same size as it was when it was launched, so when i make it bigger, there's just empty grey space.

Please help, Pricey

---

### Post by jeremy on 2005-10-27
That happened to me too for a few days, but then it just worked, I can't remember if it was after rebooting, or restarting x or what...

---

### Post by budluva04 on 2005-10-27
ya i have this same problem too, i installed java 1.5 via apt, and i've rebooted a couple times now, still has the resize problem, dont know where the bug is but azureus never did that in hoary, breezy problem maybe?

ps a fix would be nice, anyone? :P

---

### Post by jamesford on 2005-10-27
the problem is with the java. grab suns java and the problem is gone.

look here for complete instructions [http://ubuntuforums.org/showpost.php?p=423531&postcount=20](http://ubuntuforums.org/showpost.php?p=423531&postcount=20)

---

### Post by sevenrechlin on 2005-11-09
Two ways I've gotten this to work:

1. Resize the window to what you need it (or want it) to be, then go to file -> restart azureus.  Should reload fitting the window size you set.  Problem is you have to do this each time.

2. A permanent fix is this: Go to plugins and download the AZCVSUpdater plugin, and download the newest CVS version.  Afterwards, it should work perfectly fine.

---

