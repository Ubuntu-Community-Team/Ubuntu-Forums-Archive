---
title: "plymouth and GDM3 distorted during start up"
date: 2018-11-25
forum: General Help
---

### Post by dmbomer on 2018-11-25
Ubuntu 18.04
Amd 8230
MSI RX570

dmbomer@deepcool:~$ uname -a 
Linux deepcool 4.15.0-39-generic #42-Ubuntu SMP Tue Oct 23 15:48:01 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
dmbomer@deepcool:~$ inxi -G
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Ellesmere [Radeon RX 470/480]
           Display Server: x11 (X.Org 1.19.6 ) driver: amdgpu Resolution: 2560x1080@74.99hz
           OpenGL: renderer: Radeon RX 570 Series (POLARIS10 / DRM 3.23.0 / 4.15.0-39-generic, LLVM 6.0.0)
           version: 4.5 Mesa 18.0.5
dmbomer@deepcool:~$ 

This only happens on start up.  If auto login is set and when I login out nothing is wrong.  User profiles are clear.

I found this [https://askubuntu.com/questions/1029784/ubuntu-18-04-missing-letters-in-login-screen](https://askubuntu.com/questions/1029784/ubuntu-18-04-missing-letters-in-login-screen)

[COLOR=#242729][FONT=Arial]by editing /etc/gdm3/custom.conf and uncommenting:[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]#WaylandEnable=false

and restarting the computer GDM3 is now fine.  

But plymouth is still distorted that is the next problem to fix.[/FONT][/COLOR]

---

