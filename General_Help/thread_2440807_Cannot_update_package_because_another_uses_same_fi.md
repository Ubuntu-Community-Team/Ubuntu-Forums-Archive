---
title: "Cannot update package because another uses same file?"
date: 2020-04-15
forum: General Help
---

### Post by nefcairon on 2020-04-15
Hello,

I currently use Kubuntu 20.4 beta for a few weeks now because I like KDE much more than Gnome which was the desktop environment on my first Ubuntu for several months. When updating via Discover I get the following error message:
```
Error while installing package: trying to overwrite '/usr/share/locale/ar/LC_MESSAGES/libksmtp5.mo', which is also in package libkpimsmtp5.
```

And discover doesn't install any packages.... 

What should I do? 

Thanks for your help!

---

### Post by CelticWarrior on 2020-04-15
Please run, in terminal ```
sudo apt update && sudo apt full-upgrade
``` and post any error messages.

---

### Post by nefcairon on 2020-04-16
Thanks for your reply.
Today I could fix it via ```
[FONT=monospace][COLOR=#000000]sudo apt --fix-broken install
``` (which didn't work yesterday).[/COLOR][/FONT]
Sorry to have bothered you. 

[FONT=monospace][COLOR=#000000]Maybe sometimes you just have to wait...
[/COLOR]
[/FONT]

---

