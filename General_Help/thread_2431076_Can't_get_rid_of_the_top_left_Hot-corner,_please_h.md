---
title: "Can't get rid of the top left Hot-corner, please help."
date: 2019-11-11
forum: General Help
---

### Post by krim71 on 2019-11-11
Hi guys,

I am a new Ubuntu user, I have Ubuntu 18.04 LTS version. I want to get rid of the top left hot corner feature because it annoys me every time I try to press the back button (typically in Chrome). I tried to disable it from Genome-Tweaks but every time I log out, suspend or restart it is activated again. Is there a permanent solution for this? 

Thanks.

---

### Post by Frogs Hair on 2019-11-11
Hello and Welcome!

If you are referring to activities there is an extension to remove/hide it. To install the extension you'll need the following first. It will allow you to install from the gnome extensions page.  

```
sudo apt install chrome-gnome-shell
```


[https://extensions.gnome.org/extension/744/hide-activities-button/](https://extensions.gnome.org/extension/744/hide-activities-button/)

---

### Post by krim71 on 2019-11-11
Thank you, that worked for me.

---

### Post by mc4man on 2019-11-11
You should have been able to do this in tweaks. 
Maybe because it sets the key to false as a custom key something goes awry? (likely if set. unset, reset it would hold.
In actuality disabled (false,) is the default  so simply going this would take care of instead of using an extension 

```
dconf reset /org/gnome/shell/enable-hot-corners
```
Then can be checked via
```
dconf read /org/gnome/shell/enable-hot-corners
```

---

