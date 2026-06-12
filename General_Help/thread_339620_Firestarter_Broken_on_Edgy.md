---
title: "Firestarter Broken on Edgy"
date: 2007-01-16
forum: General Help
---

### Post by dr_d on 2007-01-16
Hi.. I think there's a problem with the Firestarter package on Edgy.

The Firestarter docs say that it is supposed to load the iptables rules by default at boot time, but this doesn't seem to be happening.

The init script (/etc/init.d/firestarter) does get installed... but it is not loading.

An entry for Firestarter does not appear in System > Administration > Services.


Any suggestions?


EDIT: all i really need to do is to get "/etc/init.d/firestarter start" called when i boot up... update-rc.d didn't seem to work... how can i do with with the new boot manager in edgy?

---

### Post by david_2001 on 2007-01-16
The Firestarter firewall will only be activitated when the first run wizard has completed.  If you haven't already, try logging out and then back into your account and then checking for System | Administration | Firestarter again.  If it hasn't appeared then trying reinstalling and then logging out/in again.  If all fails, you could always start Firestarter from a console with a "sudo firestarter" command.

---

