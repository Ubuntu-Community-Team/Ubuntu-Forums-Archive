---
title: "Num Lock starts Disabled"
date: 2023-11-17
forum: General Help
---

### Post by rebeltaz on 2023-11-17
Ever since I upgrade my shop computer from 18.04 to 20.04.6 LTS, the computer starts up with Num Lock disabled. I have checked BIOS and it is enabled there. I have also noted that Num Lock IS enabled when the computer itself starts, but as soon as Ubuntu loads, it disables Num Lock. I have looked, but I cannot find a setting to change that. Can some kind soul help me here? This is annoying!

---

### Post by #&amp;thj^% on 2023-11-17
First be sure numlock is installed:
```
sudo apt install numlockx

```
Make Gnome honor that:
 ```
gsettings set org.gnome.desktop.peripherals.keyboard remember-numlock-state true

```
Let us know if that works.

---

### Post by rebeltaz on 2023-11-17
> **1fallen said:**
> First be sure numlock is installed:
```
sudo apt install numlockx

```
Make Gnome honor that:
 ```
gsettings set org.gnome.desktop.peripherals.keyboard remember-numlock-state true

```
Let us know if that works.

numlockx was NOT installed. I went ahead and ran those steps. I can't shut this down to test it, so I'll report back tomorrow if it worked. Most likely did. Just curious why that changed during the upgrades? 

Thanks.

---

### Post by #&amp;thj^% on 2023-11-17
> **rebeltaz said:**
> Just curious why that changed during the upgrades? 

Thanks.

i wish I had a answer, I've been scratching my head on many things lately.
**Rant coming on hide your eyes**, it just feels like we have a whole bunch of rookies lately.
Been here since 2005 and I've not seen so many bad Canonical choices.
Just might be time for me to move along.
Rant over....

---

### Post by rebeltaz on 2023-11-20
I;m sorry. I forgot to reply back. This did indeed fix it. Thank you again. You don't know how aggravating that one little thing was!

---

