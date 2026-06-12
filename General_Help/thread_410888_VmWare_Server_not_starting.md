---
title: "VmWare Server not starting"
date: 2007-04-16
forum: General Help
---

### Post by eclipca on 2007-04-16
Hello

I have Ubuntu Edgy installed, and I'm relatively new on Linux. A couple of weeks ago I installed VmWare server to do some Windows XP and Server 2003 testing. I have installed Windows XP and everything worked fine, until about one week ago. Now when I try to start VmWare Server it seems to start, says "VmWare Server console - Loading application..." in the systemtray. Then it suddenly just dissapears from the systemtray. 

I have a HP Laptop with Intel Dualcore CPU and 1GB RAM. I have tried to start it in both Gnome and KDE.

What is happening, and what can I do?

I'm not very happy with reinstalling, because then I guess I have to reinstall the XP-client also... :(

---

### Post by Tanoku on 2007-04-16
First off, reinstalling may be a wise idea since the virtual machines (aka "your Windows XP client") are stored separately and don't get erased when you uninstall VMWare Server.

Either way, if you do not want to reinstall, then I suggest you try launching the server from the console terminal and posting here what error messages do you get.


*edit* Ok, let's try to predict your answer: If it's anything Kernel related (have you upgraded your kernel recently?) then running

```
sudo /usr/bin/vmware-config.pl
```

should fix all your problems. Either way, I suggest you run the config script either way, seems to fix most common problems.

---

### Post by eclipca on 2007-04-16
Thank you!

That command fixed the problems!

---

