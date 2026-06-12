---
title: "lubuntu 22.10 keeps going to sleep"
date: 2022-12-17
forum: General Help
---

### Post by mixtutor on 2022-12-17
Guys, i try this
```
[COLOR=#525960][FONT=-apple-system]sudo systemctl mask sleep.target suspend.target hibernate.target hybrid-sleep.target[/FONT][/COLOR][COLOR=#525960][FONT=-apple-system]gsettings set org.gnome.desktop.lockdown disable-lock-screen 'true'[/FONT][/COLOR]
[COLOR=#525960][FONT=-apple-system]gsettings set org.gnome.desktop.screensaver lock-enabled false[/FONT][/COLOR]
[COLOR=#525960][FONT=-apple-system]gsettings set org.gnome.desktop.session idle-delay 0[/FONT][/COLOR]
[COLOR=#525960][FONT=-apple-system]gsettings set org.gnome.desktop.screensaver ubuntu-lock-on-suspend 'false'[/FONT][/COLOR]
```

but lubuntu keeps going to sleep mode. Any ideas?

---

### Post by ne29914 on 2022-12-17
What do you mean by "sleep"?
Suspend? 
Screensaver with black screen?
Screen blanking?

---

### Post by mixtutor on 2022-12-17
monitor goes to NO SIGNAL, and after i move mouse, background is here again.

---

### Post by ne29914 on 2022-12-17
That's screen blanking. Nothing to do with suspend, hibernate or screensaver.
Check your power saving settings.

---

### Post by mixtutor on 2022-12-17
how is that possible, system is the same, but hardware is different? When I install on one hardware there is that kind of issue.

---

### Post by mixtutor on 2022-12-19
i tried with this

I checked:
xset -q | awk '/DPMS is/ {print $NF}'
Disabled

this is what i enter.
xset dpms 0 0 0 && xset -dpms  && xset s off && xset s noblank

but didn't help.

---

### Post by TenPlus1 on 2022-12-19
I've always had issues with Lubuntu and screen blanking even when it's all disabled, ended up installing xfce's power manager and setting to presentation mode, and currently using Enlightenment desktop which handles power saving better.

---

### Post by mixtutor on 2022-12-19
thats also option, but let wait for somebody, maybe have answer.

---

