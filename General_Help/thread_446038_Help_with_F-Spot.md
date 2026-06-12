---
title: "Help with F-Spot"
date: 2007-05-16
forum: General Help
---

### Post by 67GTA on 2007-05-16
I can't get F-Spot to run. This has been a problem since I installed Feisty. It always worked in Edgy. It would never start by clicking the menu icon and the PC would run full throttle until I rebooted. I tried opening in a terminal to try to see if there was any error messages and it said it could not get a connection to dbus and then try again(over and over) hence the PC going crazy. I tried to reinstall via synaptic with no luck. Can someone shed some light on this?

---

### Post by 67GTA on 2007-05-16
I found a weird solution, but it worked in case someone else is having trouble.

[https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/95318](https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/95318)


Run in terminal:
rm -rf ~/.gnome2/f-spot

---

