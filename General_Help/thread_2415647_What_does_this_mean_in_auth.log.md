---
title: "What does this mean in auth.log?"
date: 2019-03-29
forum: General Help
---

### Post by @gw7tppYFG6 on 2019-03-29
```
Mar 29 15:18:50 ubuntu gdm-password]: gkr-pam: unlocked login keyring
Mar 29 15:44:04 ubuntu PackageKit: uid 1000 is trying to obtain org.freedesktop.packagekit.package-remove auth (only_trusted:0)
Mar 29 15:44:10 ubuntu polkitd(authority=local): Operator of unix-session:2 successfully authenticated as unix-user:ubuntu to gain TEMPORARY authorization for action org.freedesktop.packagekit.package-remove for system-bus-name::1.100 [/usr/bin/gnome-software --gapplication-service] (owned by unix-user:ubuntu)
Mar 29 15:44:10 ubuntu PackageKit: uid 1000 obtained auth for org.freedesktop.packagekit.package-remove
```

I found this after I left it alone somewhere where I couldn't see it (which is a mistake on my part) and I'm having a hard time understanding what happened here. Before 16:00, someone messed with Ubuntu and apparently installed then uninstalled something and I don't know what is what they installed/uninstalled and I don't know what they did with Ubuntu nor know what they were achieving here. Before 15:18 and after 15:44, I took hold of it and it was in sleep mode. 

Is there some sort of malware that you put on Ubuntu then uninstall or did they try and failed instead? Should I be worried and try to do something? Also, what should I check to see what was changed in Ubuntu?

---

### Post by Rubi1200 on 2019-03-30
Hi and welcome to the forums!

Are there other people who know or have access to your login password?

Thanks.

---

