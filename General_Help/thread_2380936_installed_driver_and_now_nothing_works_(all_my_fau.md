---
title: "installed driver and now nothing works (all my fault)"
date: 2017-12-24
forum: General Help
---

### Post by flames0470 on 2017-12-24
ok so total noob at Linux in general I was trying to improve my experience with a non default graphics driver but I am thinking that I got one that is not for my hardware... Anyway I need to undo the installation of that driver but when I start up the computer it goes to a login screen (which is not normal, usually it just goes to the desktop) where I type in my password and hit enter the screen goes black with a single line of writing in the corner that blinks by too fast to read and then back to the login screen waiting for my password again and I can not access the terminal while on the login screen. I have an ubuntu flash drive and can load up the try out ubuntu from that. When installing the driver I followed the directions on [http://support.amd.com/en-us/kb-articles/Pages/AMDGPU-PRO-Install.aspx](http://support.amd.com/en-us/kb-articles/Pages/AMDGPU-PRO-Install.aspx)   after the second reboot I found myself at the login screen as I described above and I have tried to run the uninstall (amdgpu-pro-uninstall) while on the flash drive but I just get the error message command not found. I am not sure what other information you may need to help me if any, hopefully this is way easier than I think it is, thanks in advance for all the help.

---

### Post by QIII on 2017-12-24
Hello!

Could you let us know what hardware you have?  That will keep us from just making stabs in the dark.

---

### Post by flames0470 on 2017-12-24
[AMD/ATI] Turks PRO [Radeon HD 6570/7570/8550] 90% sure it is the 6570


inside of a dell optiplex gx620
Intel® Pentium(R) D CPU 3.60GHz × 2

oh also the driver i used was amdgpu-pro-17.40-492261

when I look at the details in settings on the flash drive version it says for graphics Gallium 0.4 on AMD TURKS (DRM 2.49.0 / 4.10.0-28-generic, LLVM 4.0.0)

---

### Post by mörgæs on 2017-12-24
> **flames0470 said:**
> [AMD/ATI] Turks PRO [Radeon HD 6570/7570/8550] 90% sure it is the 6570


Let's get the last 10%. Please run ```
lshw -C video
``` and post the results in CODE tags.

---

### Post by flames0470 on 2017-12-24
```
ubuntu@ubuntu:~$ lshw -C video
WARNING: you should run this program as super-user.
  *-display               
       description: VGA compatible controller
       product: Turks PRO [Radeon HD 6570/7570/8550]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:27 memory:e0000000-efffffff memory:fe9e0000-fe9fffff ioport:dc00(size=256) memory:c0000-dffff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
```

---

### Post by Yellow Pasque on 2017-12-24
You can't press Ctrl+Alt+F1 to get to the terminal?

---

### Post by flames0470 on 2017-12-24
Ok yes I did not know about that I usually use Ctrl+Alt+T to get to the terminal

---

### Post by flames0470 on 2017-12-24
Yes from there it accepted the uninstall command

Thank you so much!! Everything is working correctly again. Thank you thank you thank you everyone

---

