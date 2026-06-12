---
title: "Permissions issues with ubuntu 13.10 upgrade"
date: 2014-01-24
forum: General Help
---

### Post by caffeine. on 2014-01-24
I recently upgraded to 13.10, and have a number of problems with permissions:
* Sound not working (defaults to "dummy output")
* Graphics card defaults to llvmpipe rather than Intel
* "Not authorized to control networking" when trying to connect to wireless
* Ethernet does not reconnect after suspend
* Unable to shut down or restart

The first two I have been able to temporarily fix by changing permissions in /dev/snd and /dev/dri, but this is a hack. From searching around, the more general solution seems to be to run pam-auth-update, which does nothing for me. 

Does anyone have suggestions for other strategies to try?

---

