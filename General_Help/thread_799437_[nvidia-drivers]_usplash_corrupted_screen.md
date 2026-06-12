---
title: "[nvidia-drivers] usplash corrupted screen"
date: 2008-05-19
forum: General Help
---

### Post by juliorieger on 2008-05-19
Hi,

I am using Ubuntu Hardy 8.04 on Laptop HP Pavilion dv9000 (Geforce Go 6150). When I install the last nvidia drivers I start to get some problems with usplash (for restart and suspend/hibernation). When I restart the laptop the screen initially turns black and then some white lines appear and turn white all the screen. Same problem happen when I enter the command "sudo usplash" from a terminal under Gnome, and when I press CTRL+ALT+F1.

I tried to install the older nvidia drivers and then the problem disappear but another problems came, like little freezes because xorg are using 100% cpu performance.

There is someone with the same problem? Can anyone help me?

Thanks

---

### Post by sdennie on 2008-05-19
My laptop also sometimes gets a white screen after suspend/resume.  It turns out that the unlock dialog is actually showing and if you blindly type your password into the white screen, the system will come back.

---

