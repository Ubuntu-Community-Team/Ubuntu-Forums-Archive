---
title: "Missing older Nvidia driver in Software &amp; Updates"
date: 2018-05-25
forum: General Help
---

### Post by ubuntini2 on 2018-05-25
Hi
Trying to rollback to an earlier Nvidia driver but it is NOT listed any more under Software & Updates > Additional Drivers

see attched


How can I roll back to driver 390.48 from Software & Updates > Additional Drivers if it isn't listed?

[ATTACH=CONFIG]279847[/ATTACH]

---

### Post by Autodave on 2018-05-25
Should be listed in SYNAPTIC.

---

### Post by Yellow Pasque on 2018-05-25
What version of Ubuntu are you using? Why are you trying to roll back? 
390.59 is not in the standard 18.04 repo. Did you use a PPA (like [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) ) to get 390.59?

Synaptic definitely gives you more control. Be careful when rolling back or forcing versions though. If you see '500 packages to be removed', don't click Apply. ;)

---

### Post by ubuntini2 on 2018-05-25
Thanks
Houdini crashes on launch with more recent drivers
Running 17.10
Not familiar with Synaptic

---

### Post by Yellow Pasque on 2018-05-27
If you're running 17.10, you must have used a PPA to get 350.59, correct?

---

