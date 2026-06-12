---
title: "Firestarter boot fails"
date: 2006-10-18
forum: General Help
---

### Post by Hyperion on 2006-10-18
Hi.When booting,in the list of processes that are loaded,i see the entry "Firestarter firewall failed".Then when i enter the desktop,Firestarter isn't running and when i manually launch it,i get an error message that the Firewall failed to start by unxecpected error.Once i open it though,it does seem to run,cause in Shields up i m stealthed.

I m a newbie with Linux in general,so i m not sure what i have to do.I searched the forum,but i didn't find another post with failing at boot.

I also found a command with firestarter -restart or something.The shell says "firestarter stoppin OK,restarting failed".

Thank you

---

### Post by Hyperion on 2006-10-18
Oh well,i had an automount problem with a SATA disk and read a post from this forum on how to fix it,unistalled some packages,reistalled some and now on boot i see for less than a second "failed" that soon enough becomes "ok".Still firestarter won't load automatically,but i launch it manually and seems to work.

---

### Post by DaveNF2G on 2006-10-20
I don't know if my situation is similar in any way, but Firestarter does not automatically start the firewall when I boot to Ubuntu Edgy Eft.  I have to start it manually.

Is there a fix for this?

EDIT:  This behavior is confined to Gnome.  KDE will start Firestarter on bootup.

---

### Post by Rob_H on 2006-10-21
Are you using NetworkManager? If so, this is a [known problem]("https://launchpad.net/distros/ubuntu/+source/firestarter/+bug/42759"), but you can get it to work with a custom NM dispatcher script. See the link for details.

---

