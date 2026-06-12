---
title: "Login keeps going back to login screen when xserver-xgl is installed."
date: 2007-11-06
forum: General Help
---

### Post by lynxus on 2007-11-06
Hi guys, bit of a problem.

i think everything is running normally i have my IBM R51 running on the radeon driver like before on 7.04 and everything setup the same ( New install btw )

However when i login it seems to do nothing then go back to the login screen.

This only happens on the when i have xserver-xgl installed.

This is the only thing i can find in the logs.

Nov  6 16:00:51 oken-trumpet gdm[5073]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0



Any ideas?
Thanks
graham

---

### Post by myfigurefemale on 2008-04-04
i have the same problem.  how do i rollback that install?  thanks for any help!  i really don't want to have to re-install ubuntu.  i'm a new user and it's taking me forever to get everything working right.

---

### Post by myfigurefemale on 2008-04-23
i've been trying to get compiz working for weeks on ubuntu and have had to re-install a few times due to the huge mess i made.  everything i did created problems such as:
a blank boot up screen (after installing the proprietary driver)
logging in, going to the desktop for 1 second and back to the login screen...repeatedly until i re-installed ubuntu (after using the open-source driver)
"the composite extension is not available"
"advanced desktop effects could not be available"
ect, ect.
after i installed hardy (i wiped the hardrive) i installed the [envy]("http://www.albertomilone.com/nvidia_scripts1.html") package it installed the correct ati driver for my machine.  compiz is enabled by default in hardy, so all i had to do was install the compiz-manager (in the repositories) and PRESTO!  everything finally worked.  so to anyone else who has these problems, try this...it might help!

---

