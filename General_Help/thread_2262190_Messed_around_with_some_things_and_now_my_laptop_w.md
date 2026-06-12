---
title: "Messed around with some things and now my laptop won't hibernate, it just shuts down"
date: 2015-01-23
forum: General Help
---

### Post by Number703 on 2015-01-23
Specs: HP 2000 Notebook PC 2000-2c20DX 2nd Generation Intel Core i3-2328M Processor (2.2 GHz)
Ubuntu 14.04


I got tired of my computer hibernating when it gave the critical battery warning even if I plugged it in immediately, so I tried to find a way to get the warning earlier so I'd at least have a minute to plug it in before it hibernated. Instead, I just made it worse and now it shuts down completely. I'm not sure which triggered it, but these are two sets of commands I entered, I can't remember but the second set might have been after hibernate stopped working:

```
gsettings set org.gnome.settings-daemon.plugins.power percentage-critical 10
gsettings set org.gnome.settings-daemon.plugins.power percentage-action 9
gsettings set org.gnome.settings-daemon.plugins.power use-time-for-policy false

```
```
gsettings set org.gnome.settings-daemon.plugins.power percentage-low 30


gsettings set org.gnome.settings-daemon.plugins.power percentage-critical 20
gsettings set org.gnome.settings-daemon.plugins.power percentage-action 15
```


Looking for solutions, I saw a "sudo pm-hibernate" command. Entering that, the computer completely shuts down instead of hibernating, but, when I boot back up my windows and everything are the same as if I had hibernated. 

In the power options, the "When power is critically low" option has "Hibernate" selected but it's grayed out. The only other option is to power off.

---

