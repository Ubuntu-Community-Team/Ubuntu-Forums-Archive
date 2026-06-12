---
title: "Ubuntu login black screen"
date: 2015-04-12
forum: General Help
---

### Post by andymwat on 2015-04-12
After installing the nvidia-349 package from the xorg-edgers ppa, Ubuntu boots into a completely black login screen, even the backlight for the screen is off. However, I can blindly type my password, press enter, and I successfully log in to my desktop. What can I do to fix this and get my login screen back?

I'm running Ubuntu 14.10 on a lenovo y50 laptop, with a nvidia 860m GPU, as well as Intel integrated graphics.

---

### Post by user_of_gnomes on 2015-04-12
Have you tried pressing [SHIFT]("https://wiki.ubuntu.com/RecoveryMode") before Ubuntu boots and then proceeding to boot normally (there's an option for that in the list). This worked for some videocard problems I had, allowing me to switch back to the open source drivers and try again because it interrupts the loading of the videocard drivers in some way.

---

### Post by andymwat on 2015-04-13
> **user_of_gnomes said:**
> Have you tried pressing [SHIFT]("https://wiki.ubuntu.com/RecoveryMode") before Ubuntu boots and then proceeding to boot normally (there's an option for that in the list). This worked for some videocard problems I had, allowing me to switch back to the open source drivers and try again because it interrupts the loading of the videocard drivers in some way.
That worked, but the nvidia driver (as well as anything that has to do with OpenGL) doesn't work if I do that.

---

### Post by user_of_gnomes on 2015-04-14
> **andymwat said:**
> That worked, but the nvidia driver (as well as anything that has to do with OpenGL) doesn't work if I do that.

Exactly, now you can revert back to the open source drive, reboot the system and start from scratch. I had to do that once with my ATI drivers and the second time around they did work properly.

You might find the following useful:

> **Vladlenin5000 said:**
> Youbshouldn't have to go about it manually, with Synaptic or any other tool... And the previous post says *IF* you had proprietary nividia drivers in use *THEN* you must uninstall (actually purge) them before swapping to an ATI/AMD or other, because otherwise you'll have some not-so-easy-solvable problems. 

Now, if you had the open source driver for nvidia you don't even need that, simply take one out and put the other in. If proprietary AMD drivers are required then you need to install them, just like you would anyway.

The broken packages you have now may or may not be related to what you did (uninstalled or tried to) before with Synaptic (it probably IS related). If I remember correctly Synaptic has a function for that, check the menus. Otherwise:
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get install -f
sudo apt-get upgrade
sudo apt-get remove -purge nvidia*  (just in case...)

```

Last line should probably be sudo apt-get purge nvidia*.

---

