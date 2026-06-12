---
title: "Gnome Shell Extensions disabled -  don't know why"
date: 2022-04-04
forum: General Help
---

### Post by kurt18947 on 2022-04-04
Has anyone had this happen and figured out why? I've had gnome shell extensions become disabled and have no idea why.  After some searching I came upon this solution to re-enable extensions:

```
gsettings set org.gnome.shell disable-user-extensions false
```

If I wanted to disable extensions it's similar:

```
gsettings set org.gnome.shell disable-user-extensions true
```

I've had it happen twice. The first time was a few months ago and just today. It's a simple fix but I wonder why it happens. I didn't install any new software or any new extensions. I do update frequently but I don't think this is related to updates.

---

### Post by Dennis N on 2022-04-04
> I wonder why it happens. I didn't install any new software or any new extensions. I do update frequently but I don't think this is related to updates. 
When some extensions are updated, the extensions are automatically all switched off. If you open the **Extensions** app, the switch at the top will turn them all back on. No need to use terminal commands.

---

### Post by kurt18947 on 2022-04-04
> **Dennis N said:**
> When some extensions are updated, the extensions are automatically all switched off. If you open the **Extensions** app, the switch at the top will turn them all back on. No need to use terminal commands.

Thanks for your reply. I'm not familiar with any Extensions app, I use the extensions web site. Are you referring to the Tweaks app? I've had the extensions turn themselves off as you mentioned but simply moving the 'switch' to on fixed it. This didn't work in this case, the 'sliders' in the Tweaks extensions page were grayed out and the switches on the web page were inactive.

---

### Post by Dennis N on 2022-04-04
"Extensions" is installed with this package in Ubuntu 20.04:
```
dmn@Sydney:~$ apt show gnome-shell-extensions
Package: gnome-shell-extensions
Version: 3.36.1-1
Priority: optional
Section: universe/gnome
Origin: Ubuntu

```
I've had the same thing happen a number of times, and was able to turn them back on as I described.

---

### Post by kurt18947 on 2022-04-05
Thanks Dennis. I'll have to install that.

---

### Post by iamjiwjr on 2022-04-05
Same here. Neither snap or flatpak firefox would work. But.... I got the gnome extensions to activate via the Chrome Browser. I installed Chrome's Gnome Shell Integration add-on. Then I clicked on it and the Gnome extensions were activated so I could install extensions.

---

