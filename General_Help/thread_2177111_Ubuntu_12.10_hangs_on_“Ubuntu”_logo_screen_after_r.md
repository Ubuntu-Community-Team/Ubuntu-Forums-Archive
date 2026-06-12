---
title: "Ubuntu 12.10 hangs on “Ubuntu” logo screen after running Ubuntu Tweak' “Janitor” tool"
date: 2013-09-27
forum: General Help
---

### Post by Mark_Bates on 2013-09-27
[I originally posted this on AskUbuntu: ]("http://askubuntu.com/questions/350629/ubuntu-12-10-hangs-on-ubuntu-logo-screen-after-running-ubuntu-tweaks-janitor")

> I dual-boot Ubuntu 12.10 and Windows 7 64-bit. Previously I had no issues. Tonight I ran Ubuntu-Tweak's "Janitor", which cleaned old packages and such from my Ubuntu partition. When I rebooted, Ubuntu would not boot past the "Ubuntu" splash screen (the dots would fill up, and then the system would hang there). I can boot into Windows 7 just fine. I can also get to the recovery mode command line. I'm afraid that Ubuntu-Tweak "Janitor" uninstalled something crucial to booting.

What to do? Thanks in advance for your help.


---

### Post by mut3d87 on 2013-09-27
go into the grub menu and edit the boot line remove quiet and splash to see where and what is hanging.

---

### Post by ibjsb4 on 2013-09-27
Janitor is known to do that.  In the future use [Bleachbit]("https://apps.ubuntu.com/cat/applications/quantal/bleachbit/"), I have been using it for years without this issue.

As for your current problem, try this in terminal:

```
sudo apt-get install --reinstall ubuntu-desktop
```

---

### Post by Mark_Bates on 2013-09-27
> **mut3d87 said:**
> go into the grub menu and edit the boot line remove quiet and splash to see where and what is hanging.

I will try this when I get home, but how exactly would I change this? I should have mentioned that I tried sudo apt-get install --reinstall ubuntu-desktop already through the recovery terminal.

---

