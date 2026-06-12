---
title: "How Do I Make Unity The Default Ubuntu 17.10?"
date: 2017-12-27
forum: General Help
---

### Post by kamrynborden on 2017-12-27
I just did a fresh install of Ubuntu 17.10 on my main desktop. Every time I log in, Gnome is the default. On any other computer, if I selected Unity from the Login Menu, it always stayed the default. I tried removing Gnome, then it would get past the clearing blocks during boot.
All of the computers are set up the same, software-wise.

Specs:
Motherboard: ASUS Z97-K
Processor: Intel Core i3-4130
Graphics: Integrated
RAM: HyperX Fury 8GB DDR3 1833 MHz
Drive: SAMSUNG 850 EVO 250GB M.2

---

### Post by mc4man on 2017-12-31
If you did a fresh install then unity is not included. Here are the exact steps i'd use from a _fresh install_. (done on 18.04 but no different than 17.10
Install Ubuntu, when installing make sure to require password to login, i.e. no autologin.
Login to the xorg session 
Open a terminal run these commands
```
sudo apt update && sudo apt upgrade
```
```
reboot
```

When back login again to xorg session
```
sudo apt purge gdm3
```
```
sudo apt install lightdm unity
```
```
reboot
```
Now at the login there will be 4 options, unity is the last one, pick that

I'd generally suggest that if using unity get rid of gnome-shell, then at login there won't be any choices
```
sudo apt purge gnome-shell
```
```
reboot
```

There are a few little inconsistencies, workarounds & or improvements are possible but that's not your question.

---

