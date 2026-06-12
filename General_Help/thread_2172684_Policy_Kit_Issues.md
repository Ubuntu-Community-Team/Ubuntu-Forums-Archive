---
title: "Policy Kit Issues"
date: 2013-09-06
forum: General Help
---

### Post by gdi2k on 2013-09-06
Greetings, 

I think I'm having an issue with Policy Kit. Whenever I try to install updates from the GUI update manager, or install additional languages, it fails. I get errors like this when installing additional languages for example: 

```
org.freedesktop.PolicyKit.Error.Failed: ('system-bus-name', {'name': ':1.56'}): org.debian.apt.install-or-remove-packages
```

The GUI update manager just crashes silently. 

This started after I reinstalled, but kept my previous home directory on another partition. Maybe to do with groups or UIDs or something? 

In case it matters, I use xubuntu as the base with openbox on top. 

Any ideas?

---

### Post by gdi2k on 2013-09-06
Ah, it's easy when you know how ;)

Due to using openbox, not Xubuntu's preconfigured XFCE, the PolicyKit Authentication Agent was not being started. This must be running for things to work apparently. Adding: 
```
/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
```

to start up applications fixes the issue.

---

