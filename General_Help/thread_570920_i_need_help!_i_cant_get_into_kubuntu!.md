---
title: "i need help! i cant get into kubuntu!"
date: 2007-10-08
forum: General Help
---

### Post by taehC on 2007-10-08
hi i use kubuntu and use the restricted drivers for nvidia.  i noticed that there is no restricted drvier manager like there is in ubuntu but i didnt really think about it.  now the latest update just messed up my system because there was no driver manager(or i atleast think that is the reason.) so if anyone could help me fix it and show me a way to permanetly have a fix that would be great!

---

### Post by Pumalite on 2007-10-08
Ctrl+Alt+F1 to get a command line if you don't have one

sudo dpkg-reconfigure xserver-xorg, choose 'vesa' as the driver, then: startx

---

### Post by Les_Caesars on 2007-10-08
Did you originally have Ubuntu and -then- install Kubuntu? Perhaps you could install ubuntu_desktop and attempt to solve the problem through gnome.

the command you would use is

```
sudo apt-get install ubuntu-desktop
```


But then again, what do I know?

---

