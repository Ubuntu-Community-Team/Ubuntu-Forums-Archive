---
title: "Ubuntu 22.04 LTS GPU Passthrough problem"
date: 2022-05-17
forum: General Help
---

### Post by Sandi1987 on 2022-05-17
[COLOR=#353C41]I have NVIDIA GeForce RTX 30 Series and AMD Ryzen 5600X.[/COLOR][COLOR=#353C41][FONT=&amp]

I installed Ubuntu 22.04 LTS and GPU Passthrough not working anymore. Black screen with some lines on screen and computer freeze when i start VM in KVM. Worked fine in Ubuntu 21.10. Any solution? Maybe [/FONT][/COLOR][COLOR=#353C41][FONT=&amp]because Single GPU/Single Monitor, NVIDIA Drivers, Kernel, hooks or latest Ubuntu is the problem?

[/FONT][/COLOR][COLOR=#353C41][FONT=&amp]It worked with Single GPU and Single Monitor in Ubuntu 21.10.[/FONT][/COLOR][COLOR=#353C41][FONT=&amp]
[/FONT][/COLOR]

---

### Post by ajgreeny on 2022-05-17
Are you logging in to a wayland or X11/xorg session?
Waland is the default and this may be behind your problem; try logging in to an X11 session at the login screen.

---

