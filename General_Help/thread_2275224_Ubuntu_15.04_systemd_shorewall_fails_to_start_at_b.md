---
title: "Ubuntu 15.04 systemd shorewall fails to start at boot."
date: 2015-04-24
forum: General Help
---

### Post by edwardecl on 2015-04-24
Just want to let you guys know that shorewall does not run at boot at least for me after and upgrade to 15.04 from 14.10.

I have found a fix on the debian forum that works in this case.
[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=773392](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=773392)

The fix is to edit "/etc/init.d/shorewall"
and change
"# Default-Start:     S"
to
"# Default-Start:     2 3 4 5"

then run 

sudo update-rc.d shorewall remove
sudo update-rc.d shorewall defaults

Which then allows shorewall to start, for anyone else having issues with shorewall on 15.04.

---

