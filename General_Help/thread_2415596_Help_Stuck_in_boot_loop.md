---
title: "Help Stuck in boot loop"
date: 2019-03-28
forum: General Help
---

### Post by naiqor0-people on 2019-03-28
Ubuntu 18.10 whilst in chrome gnome extensions inadvertently turned off dash to dock, machine immediately went into reboot and then a boot loop at password entry. This happens if i try to boot into gnome, Gnome Classic, Gnome Xorg (which I use), Ubuntu or Ubuntu on Wayland, but will boot in mate but can do nothing with it. As I cannot get pass password boot loop cannot get into change it.
Thank you.
Brian

---

### Post by kc1di on 2019-03-28
[This page]("https://www.maketecheasier.com/fix-ubuntu-login-loop/") may help.

---

### Post by naiqor0-people on 2019-03-29
Thanks for that, it got me into the terminal, but it was talking about Xauthority, but my system said not found. I just turned dash to dock of, surly there is a command you can type in to just turn it on again. Tried to install gnome shell etc but it said none to down load none to update, so it must be still all there.

---

### Post by wiggers2 on 2019-03-31
Had the same problem after (recklessly) upgrading to 19.04. After eliminating the usual issues and establishing I could log in by creating a new account. So the system was OK. I finally found the culprit. It was an extension which stopped gdm3. First I removed all of gnome-shell. That let me log in. Next I refined my search and only removed .local/share/gnome-shell/extensions/'extension@abteil.org'. Everything now works fine. I have not yet tried to figure what the offending extension does.
Took me a few hours though.

---

### Post by kc1di on 2019-04-01
Glad you got it going :)

---

### Post by naiqor0-people on 2019-04-06
Thank you to the people that offered help, it was much appreciated, as i learnt a lot. 
I partially solved the problem by using sudo apt-get remove gnome-* in a terminal, then when that finished sudo apt-get install gnome-shell rebooted when that finished. Did get ubuntu back, but it looks like a reinstall of ubuntu to get every thing back together properly. So will wait until 19.04 is out and do a clean install to the new ssd i will have by then.

---

