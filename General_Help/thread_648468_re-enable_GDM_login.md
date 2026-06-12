---
title: "re-enable GDM login"
date: 2007-12-23
forum: General Help
---

### Post by ErusGuleilmus on 2007-12-23
This is kind of embarrassing. I was messing around in my 64bit Ubuntu, and turned off something like "GDM login" from system/Administration/Services. This made it so that I could not login in at all. I am typing this from my 32bit install, and have the 64bit partition mounted. What do I need to change so that I can turn GDM login back on? Thanks.

---

### Post by quux on 2007-12-23
If you're used to the ui admin tools, the easiest way would be (i) boot your system, (ii) login on the console, (iii) do a "sudo /etc/init.d/gdm start" which should bring up your regular GDM login screen, (iv) login as usual, (v) use the admin tool to reverse your change. 

Alternatively, you should be able to re-activate it directly on the console using "update-rc.d gdm defaults 30".

---

