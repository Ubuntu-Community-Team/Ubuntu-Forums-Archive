---
title: "No root passwords prompt"
date: 2015-07-26
forum: General Help
---

### Post by miskopo on 2015-07-26
Hello dear fellows!

I recently switched from mate to unity (just installed unity-desktop and removed mate-desktop) with all dependencies and suddenly, *sudo* password prompt is gone. For example, when I try to launch Synaptic, it does absolutely nothing, or, when cleaning system with Ubuntu Tweak, it does nothing as well (it used to ask for password). But on the other hand, *gksu* and *sudo* commands work.
I have administrator rights for my account.
Any ideas what is wrong?
Thank you

Distro: Ubuntu 14.04

---

### Post by ajgreeny on 2015-07-26
Do you mean when you click on the synaptic menu item you get no GUI password prompt?
The command in the menu item for synaptic is now ```
synaptic-pkexec
``` and it does not use either sudo or gksudo any more.

I wonder if the change from Mate to unity has caused some problem in the application.desktop files being used.

Have a look in nautilus for the synaptic.desktop file and open it with gedit to see what the command being used is at the moment.  It is possible there may be more than one synaptic desktop file.

---

### Post by miskopo on 2015-07-26
Thank you for your reply, but I am afraid this problem is system-wide. As well, I can't install programs via Ubuntu Software Center, because it just doesn't ask for password thus can't continue.
Yes, the point is, I don't get GUI password prompt (except gksu command launched from terminal or alt+f2) from any application.
Nevertheless, I checked synaptic launcher and it is as you wrote.

---

### Post by miskopo on 2015-07-26
Final solution:
```
sudo apt-get install policykit-1-gnome
```

Mate has it's own policykit, so with uninstalling it was gone.

---

### Post by ajgreeny on 2015-07-26
Well done!

Now you mention the answer, I think I remember seeing this once before but I had totally forgotten.

---

