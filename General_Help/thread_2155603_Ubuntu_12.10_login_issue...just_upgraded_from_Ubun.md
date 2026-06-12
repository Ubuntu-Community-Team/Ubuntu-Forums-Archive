---
title: "Ubuntu 12.10 login issue...just upgraded from Ubuntu 12.04"
date: 2013-06-18
forum: General Help
---

### Post by TimothyLinux on 2013-06-18
I messed up bad. I've been using Ubuntu 12.04 for 2 months and it's served me well. I did the stupid thing: I decided to upgrade to Ubuntu 12.10. And now, instead of bringing up the login screen, it brings up this black screen prompting me for my username and password. It always says they are invalid. This is stupid, and I really need help. I have a Toshiba laptop with Intel Core i3. Any help would be extremely appreciated.

---

### Post by searchfgold6789 on 2013-06-18
Hi,
It sounds like this is a graphics issue. Often, something will go wrong during the upgrade and the correct driver package won't get installed.
Be sure that your caps lock key isn't on, etc. The password won't actually appear on the screen, as you've seen, so type very carefully. If the username (lowercase letter at the beginning) and password are both correct, you will get to a bash prompt.
Have you tried booting to Recovery mode from the Grub menu? If you don't normally see the Grub menu, just press and hold Shift while the computer boots. 
Once in Recovery mode, you can go to Failsafe graphics mode. If that works, you can try to use the Additional Drivers program. Recovery mode also allows you to enter a shell prompt with root access.

---

### Post by TimothyLinux on 2013-06-19
Thanks for the answer. I did get logged in, thanks. But the screen is black with white text. I think it is a graphics problem. Is there anything I can do to fix it?

---

### Post by searchfgold6789 on 2013-06-19
The next step would be to figure out what kind of graphics card you have. If you type either of the two commands, you can find out: ```
lspci | grep VGA
``````
sudo lshw -c display
```(With the second one you have to type your password again; it won't appear.) What make and model of graphics card is listed?

---

### Post by TimothyLinux on 2013-06-19
It says PCI (sysfs), it describes it as a VGA compatible controller, or a 2nd generation Core Processor Family Integrated Graphics Controller version 09. Is that good enough?

---

