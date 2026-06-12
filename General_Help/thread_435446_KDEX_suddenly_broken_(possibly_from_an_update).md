---
title: "KDE/X suddenly broken (possibly from an update)"
date: 2007-05-06
forum: General Help
---

### Post by hambone79 on 2007-05-06
I have a laptop running Kubuntu 7.04. It was running fine for several day...I was suspending to disk when I wasn't using the laptop so I never rebooted. When I finally rebooted today, I found that I am suddenly unable to login to KDE.

The weird thing is that KDM starts up just fine and I can log into a "Failsafe" session without a problem, but when I choose a KDE session the screen goes blank and flickers a few times before it kicks me back to KDM.

I can kill KDM and start KDE from the command line using "startx", but I still can not get into KDE from the KDM login.

The only thing of any use I found in the logs is a line in /var/log/Xorg.0.log that said something about "Server caught signal 11".

Does anyone know how to fix this?

---

