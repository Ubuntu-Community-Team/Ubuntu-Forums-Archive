---
title: "Server hangs on boot scripts - is this normal?"
date: 2007-08-31
forum: General Help
---

### Post by spcoex on 2007-08-31
HI all, 

I installed Ubuntu Sever 7.0.4 and everything works well. But whenever I do a reboot, it goes thru all the diagnostics (ie. starting mySQL, apache, etc) as normal  and then stops at:

*** "Running local boot scripts (/etc/rc.local)"***

I need to hit Enter/Return so I can get a login prompt - is this normal?

Pressing enter is not really a big deal, but Im just worried that when I need to reboot from a remote location, I will not be physically there to press enter. 

Thanks

---

### Post by louieb on 2007-08-31
Yes its normal. Mine does it too. The script is just a place holder for anything you might want to add at the end of boot. 

ssh-server should be up and running so you shouldn't have any trouble logging back in after a remote reboot.

---

