---
title: "snap store or the Ubuntu store"
date: 2018-10-10
forum: General Help
---

### Post by idkwhatimdoing1.0 on 2018-10-10
Hey, um accidentally i deleted a package and I'm gonna assume it was the snap store... Because now in my application menu the snap store is no there... My question is how do I install it back? Running Ubuntu 18.04 thank you!

---

### Post by deadflowr on 2018-10-10
See if it's actually still there
```
apt-cache policy gnome-software-plugin-snap
```
if not try installing the package.
You might need to kill gnome-software and start it again in order to have the feature enabled.
(The software store is always running in the background even after you close it.)

---

### Post by idkwhatimdoing1.0 on 2018-10-10
i tried that command line and it gives me ```
gnome-software-plugin-snap:
  Installed: (none)
  Candidate: 3.30.2-0ubuntu2
  Version table:
     3.30.2-0ubuntu2 500
        500 http://ca.archive.ubuntu.com/ubuntu cosmic/main amd64 Packages


```

is that good?

---

### Post by mc4man on 2018-10-10
> **idkwhatimdoing1.0 said:**
> i tried that command line and it gives me ```
gnome-software-plugin-snap:
  [COLOR="#FF0000"]Installed: (none)[/COLOR]
  Candidate: 3.30.2-0ubuntu2
  Version table:
     3.30.2-0ubuntu2 500
        500 http://ca.archive.ubuntu.com/ubuntu cosmic/main amd64 Packages


```

is that good?
Do you think the red highlighted above tells you anything?

---

### Post by idkwhatimdoing1.0 on 2018-10-10
well obviously it means something is not there. But I don't know if that is for the GUI or if its just the snap store in general. And what am I supposed to write for it to come back?

---

### Post by DuckHook on 2018-10-10
> **idkwhatimdoing1.0 said:**
> …what am I supposed to write for it to come back?
```
sudo apt install gnome-software-plugin-snap
```
After it is installed, reboot.

---

### Post by idkwhatimdoing1.0 on 2018-10-10
oh my god thats perfect! it worked! Thank you so much!

---

### Post by DuckHook on 2018-10-10
You're welcome.

FWIW, if it were my installation, I would be very careful about installing snaps:

[LIST]
[*]They don't operate under the same rules as regular apps installed into your system the regular way. This leads to added complexity and confusion, especially if you come looking for help on these forums.
[*]There have been a couple of instances of rogue apps making their way into the snap store. While this security concern can be blown out of proportion, it does lead one to question whether snap apps undergo the same level of rigorous examination that regular apps undergo.
[/LIST]
In most cases in which a regular user is likely to find themselves, it is unnecessary to use anything other than the standard repo apps. Of course, if you are a tester, experimenter or tinkerer, then anything goes, but likewise, you would then be expected to be prepared to deal with all sorts of problems and bugs.

---

### Post by idkwhatimdoing1.0 on 2018-10-11
Perfect will keep in mind, thank you!

---

