---
title: "Black screen after Grub every once and while"
date: 2018-03-05
forum: General Help
---

### Post by ib80 on 2018-03-05
Hi,

It has been a while where every so often I am greeted with a black screen right after Grub. If I reboot, by pushing the reboot button, KDE might start up, or not, depending on my luck :tongue:. Windows always boots up if I select it through the grub menu.
It has been this way for about three Kubuntu releases or so and I keep my distrib updated using official, regular and backport repositories. I waited this log as I was hoping that it would be fixed after each version upgrade :P.

My PC has a Nvidia graphics card and I have installed the nvidia-384 driver through the system settings app.
I have a dual boot with windows 10 using UEFI. I am not sure if I installed Windows first of Kubuntu as it has been a while but at the time, I searched the web on the subject and followed the instructions on how to make sure that both systems can coexist (disabling secure boot, hibernation, etc.).

I do not know where to start to try and find the root of the problem. I tried dmesg but nothing interesting there.

Any ideas of where to start?

Thanks

---

### Post by thehipho on 2018-03-05
You could start by installing Nouveau drivers and try them for your Nvidia card.

---

### Post by ib80 on 2018-03-07
Thanks thehipho.
I did just that. This time kubuntu loaded up with no hiccups.

I'll wait for a few more times before marking this subject as solved.

---

### Post by thehipho on 2018-03-12
If your issue is resolved, please mark this topic as [SOLVED]. Thanks!

---

### Post by ib80 on 2018-03-14
The issue is still not resolved. I still have a problem when trying to boot Kubuntu. It works once every two or three tries.

I might get a black screen just after grub, or the Kubuntu logo and then the black screen or, if I am lucky, the Kubuntu logo, then the desktop.
And that is only when I select the "other linux options" menu item in grub and select the latest kernel version. I just tried a few times to let the counter go to zero and select the default option but it rarely works.

When selecting the other linux options, I get some messages on the screen and I am now trying to solve them.
For example, I have a message "[Firmware Bug]: TSC_DEADLINE disabled due to Errata; please update microcode to version: 0x52 (or later)", so I just installed "intel-microcode".
I will see if this changes anything.

---

### Post by thehipho on 2018-03-14
Was your PC custom built? Is your PC being overclocked?
Could you paste the output of: ```
inxi -b
```

Another thing to try which might help is: Open '/etc/default/grub' in a text editor with 'sudo' permission.

Remove: "quiet splash" from GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
like so: GRUB_CMDLINE_LINUX_DEFAULT=""

Update grub: 
```
sudo update-grub
```
[KernelBootParameters guide.]("https://wiki.ubuntu.com/Kernel/KernelBootParameters")

reboot the PC

---

### Post by ib80 on 2018-03-15
Yes, I have built my own PC and I only activated a XMP profile for my RAM. The CPU does not support over clocking.

Here is the output of the inxi command:
```
System:    Host: sunset Kernel: 4.13.0-37-generic x86_64 bits: 64 Desktop: KDE Plasma 5.10.5
           Distro: Ubuntu 17.10
Machine:   Device: desktop Mobo: ASRock model: Z97 Extreme4 serial: N/A UEFI: American Megatrends v: P2.50 date: 07/27/2016
Battery    hidpp__0: charge: N/A condition: NA/NA Wh
CPU:       Quad core Intel Core i5-4690 (-MCP-) speed/max: 3498/3900 MHz
Graphics:  Card: NVIDIA GM204 [GeForce GTX 970]
           Display Server: x11 (X.Org 1.19.5 ) drivers: nouveau (unloaded: modesetting,fbdev,vesa)
           Resolution: 1920x1080@60.00hz
           OpenGL: renderer: NV124 version: 4.3 Mesa 17.2.8
Network:   Card: Intel Ethernet Connection (2) I218-V driver: e1000e
Drives:    HDD Total Size: 4256.9GB (35.1% used)
Info:      Processes: 214 Uptime: 13 min Memory: 1329.8/15997.0MB Client: Shell (bash) inxi: 2.3.37
```

I just updated grub to the latest available version and the GRUB_CMDLINE_LINUX_DEFAULT option now defaults to empty so I left it as it is.
I will reboot and see what happens.

---

### Post by ib80 on 2018-03-15
I had to reboot three times to be able to get to Kubuntu's desktop.

The last thing I saw in the first two boots was a message about ata7.00 exception. I'll look into it this weekend.

---

### Post by thehipho on 2018-03-17
When this happens have you tried to Ctrl+Alt+F1 to switch to a text console and log in there.
```
startx
```

---

### Post by ib80 on 2018-03-19
Yes I tried but it I don't think that it passes enough steps in the boot process where this option is available.

It seems that when it boots all the way, it gets quickly to boot kubuntu, with "[    OK]" in green at the start of each line while it is still on command-line logging.
When it does not boot all the way it gets stuck showing on-screen logs like the one from dmesg with an error on ata7.
I usually have to boot to windows 10, shutdown and restart the PC. That way, kubuntu starts once every 2 tries.

Quite weird.

---

### Post by ib80 on 2018-05-23
Hi,

I found a way around this issue. I wait for the boot process to start, and if I don't see the ubuntu startup script's log on the screen in the first 6 seconds or so, I quickly reboot using Ctrl-Alt-Del and try again. It eventually does boot.
If I wait more and it does not go through, the PC stops responding to keyboard input.

Not ideal, but this way I don't have to hard reboot, which hurts the PC on the long run.

The issue is not really fixed so I won't flag it as fixed. I hope it will some day :D

---

