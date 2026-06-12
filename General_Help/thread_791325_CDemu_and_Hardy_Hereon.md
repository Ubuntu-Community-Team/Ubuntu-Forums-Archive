---
title: "CDemu and Hardy Hereon"
date: 2008-05-12
forum: General Help
---

### Post by chungy on 2008-05-12
Has anyone else had much luck with this?

First, I tried CDemu 1.0.0, and that didn't work; vhba failed to compile.  Then I decided to try SVN (I got r315 to be specific), and it worked -- or it seemed to.

I'm able to mount a disk image fine, and access it like normal.  cdemu-client itself isn't able to unload a disk image, because HAL caught it and automounted it.  No biggie, I just right-click the desktop icon and click "Eject" (I've done it on earlier ubuntu versions in the exact same way).  AFTER these two tasks are done, however, cdemu seems to refuse to do anything else.  even typing "cdemu status" will cause... nothing at all to happen; no messages on the terminal, or anything.  Now I can mount more images if I kill the cdemu-daemon and rmmod vhba (not sure if the later is required, but why not), and repeat, but this is tedious and well, not very handy.

Does anybody else know what I'm talking about..?  Possible solutions, or is this something that probably should be sent to the CDemu team?

---

### Post by chungy on 2008-05-12
bump--anybody?

---

