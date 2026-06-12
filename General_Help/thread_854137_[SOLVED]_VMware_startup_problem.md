---
title: "[SOLVED] VMware startup problem"
date: 2008-07-09
forum: General Help
---

### Post by Stolea on 2008-07-09
I installed the VMware server as per instructions and after a few initial hiccups all ran smoothly. Because I had too little space in the root /var directory, I had to give it a custom setting "/home/peter/vmware/Virtual Machines/Windows XP Pro/WinXP" regarding where the WinXp setup was actually installed, I had to start it through "sudo vmware" in order to be able to change the settings.
Ever since if I click on the VMware icon in Applications>Systemtools>VMware the application won't start, but will when I start it through "sudo vmware".
However after loading WinXp I get the following error
```
Cannot open file "/home/peter/.vmware/preferences": Permission denied.
Unable to read user preferences.
```
I clearly have done something that I should not have. Any ideas or suggestions? or would it be easier to just uninstall VMware and start over?

---

### Post by sdennie on 2008-07-09
Often if you run apps as sudo, root will own the config files instead of your user.  That could be the case here so, try running:

```

sudo chown -R peter:peter /home/peter/.vmware

```

And then starting via the menu item and not with sudo.

---

