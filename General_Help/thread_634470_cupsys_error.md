---
title: "cupsys error"
date: 2007-12-07
forum: General Help
---

### Post by penquin on 2007-12-07
while trying to get a program I accidently installed a different cupsys.  I thought nothing of it at the time but it would not let me unistall the new cupsys unless I purged it, so I did.  In doing so I accidently unistalled ubuntu-desktop.  I wasn't worried yet I just tried to reinstall ubuntu-desktop and it gave me the error

Setting up cupsys (1.3.2-1ubuntu7.1) ...
Reloading AppArmor profiles : done.
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
                -n: not really
                -f: force
dpkg: error processing cupsys (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 cupsys
E: Sub-process /usr/bin/dpkg returned an error code (1)

It wouldn't even consider installing ubuntu-desktop without it.  how can I fix this?  I tried in recovery mode and the same response.

---

