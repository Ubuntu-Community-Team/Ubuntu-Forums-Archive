---
title: "Ubuntu 18.10 Switching to Console not working"
date: 2019-02-07
forum: General Help
---

### Post by feldim2425 on 2019-02-07
Hello.
I recently installed Ubuntu 18.10 (fresh install) and found that I can't access the Console with (Ctrl+Alt+F3,4,5,6).
It switches to a different screen but the only thing I can see are the 5 animated dots from the bootscreen and a cursor that reacts to keypresses but doesn't execute any commands and it also doesn't print anything that looks like a command line (Prints ^C instead of Terminating, has no prefix with the working directory, ...)
[ATTACH=CONFIG]282430[/ATTACH]

I have the nvidia-driver-390 driver installed, Gnome 3.30.1 and Kernel version 4.18.0-14-generic.
To allow the driver to run I had to change a line in the config (/etc/gdm3/custom.conf) to remove the # from #WaylandEnabled=false according to this question: [https://askubuntu.com/questions/1085042/ubuntu-18-10-installing-nvidia-drivers-leads-to-black-screen-after-grub](https://askubuntu.com/questions/1085042/ubuntu-18-10-installing-nvidia-drivers-leads-to-black-screen-after-grub)

Does anyone know how to fix this issue?

---

