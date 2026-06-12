---
title: "Notebook Screen-Brightness FN Keys not working anymore"
date: 2022-01-22
forum: General Help
---

### Post by petiz on 2022-01-22
Hello everyone,


Since yesterday i have the problem that the FN-Keys for the screen-brightness are not working anymore. 
I haven't changed nothing in the system-configuration. 

What i already know / i can tell you:

- The system still recognizes the keys. When i press the button, the overlay for the level of the screen-brightness in the top right corner still pops up
- I still can manually change the screen-brightness in energy-control in the xfce-panel
- I'm using Xubuntu 21.10 with the latest updates
- I had to switch to kernel 5.15.16 because of graphic-issues (i had some strange screen-flickering with with stripes with the kernel 5.13)
- After the kernel-change the FN-Buttons did still work
- I tested the kernel 5.13, but it does not solve the problem
- The Notebook is an ASUS Zenbook UM425U (AMD Ryzen 5700U CPU , Vega7 IGPU)

From a technical point of view, it looks like that somehow the "mapping" between what has to happen when i press the fn-key and the order to decrease/increase the brightness does not work anymore.



Do someone have an idea what could be the problem or can give me a few hints how to debug the problem by myself?



Thank you for your answer in advance!

---

### Post by petiz on 2022-01-22
I have got another additional information:


1.)
The path "/sys/class/backlight/amdgpu_bl0" exists a
If im installing the command light, it only works with sudo.

"sudo light -s sysfs/backlight/amdgpu_bl0 -U 10".


2.)
I added a new unix-user and with the new user, the FN-Keys are working




So it's some kind of user-profile specific permission problem

---

