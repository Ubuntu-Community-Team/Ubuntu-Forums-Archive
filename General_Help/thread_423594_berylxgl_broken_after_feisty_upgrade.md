---
title: "beryl/xgl broken after feisty upgrade"
date: 2007-04-26
forum: General Help
---

### Post by cptjaben on 2007-04-26
I just upgraded from Edgy to fiesty. After restart i booted up into my normal xgl session, and it was completely unviewable. I logged out and used my gnome session and it seems to be working fine, however it is slightly slow because xgl seems to be still running, when i try to close it the screen goes black and i get sent back to the login screen. I used [this guide]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL_and_ATI") to install beryl/xgl on egdy. Any ideas how i can get beryl up and running again or remove it completely? Thanks.

After further looking into the problem it looks as though the reason is that it switched my drivers back to the MESA drivers as opposed to the ATI ones. Previously I had used Envy to install drivers for my X1700, however it appears to be not working so my new question is, is there a way I can install new drivers easily in feisty? Thanks

---

### Post by Belyel on 2007-04-26
check out [This thread]("http://ubuntuforums.org/showthread.php?t=414194") for information on how to get your x**** card working.  Alternately, you may be able to uninstall envy, then go back to alberto milone's webpage, and get and install the new version of envy for feisty.  It worked on my desktop, and now beryl works, too.

---

### Post by cptjaben on 2007-04-27
do you know if there is a version of envy that supports fiesty?

---

