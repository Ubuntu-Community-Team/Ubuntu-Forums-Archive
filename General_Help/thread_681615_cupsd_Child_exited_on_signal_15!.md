---
title: "cupsd: Child exited on signal 15!"
date: 2008-01-29
forum: General Help
---

### Post by martininranco on 2008-01-29
Following a recent software upgrade, CUPS no longer starts, giving the message in the title.

CUPS worked previously, which surprised me, as my setup is far from normal - I am the only Linux box on a network of Macs. The printer is attached thru USB to the Apple Airport Extreme Basestation. The Macs 'see' the printer via Bonjour, but I could see it as attached to the router.

The original, and every subsequent software upgrade failed, because the cups server won't start; here's what I see

Setting up cupsys (1.3.2-1ubuntu7.5) ...
Reloading AppArmor profiles : done.
 * Starting Common Unix Printing System: cupsd                                  cupsd: Child exited on signal 15!
invoke-rc.d: initscript cupsys, action "start" failed.
dpkg: error processing cupsys (--configure):
 subprocess post-installation script returned error exit status 3

Can anyone help?

---

