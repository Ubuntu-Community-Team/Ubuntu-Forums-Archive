---
title: "Can't login after lock screen (black screen)"
date: 2016-07-24
forum: General Help
---

### Post by brunolabs on 2016-07-24
Hi!

After locking screen and monitor going into sleep mode, I can't get the login screen anymore, the monitor stays in sleep mode forever.
In previous Ubuntu versions after pressing any key or the mouse, the login screen showed up, but not anymore. I have to restart the computer. :(

How can I fix this issue?


Thanks!

---

### Post by brunolabs on 2016-08-24
Can anyone help me with this issue please?

Thank you.

---

### Post by ventrical on 2016-08-24
Could we have more info please.

PC type( hardware)
Distro you are using., ie; trusty, xenial .. etc..

Regards..

---

### Post by ventrical on 2016-08-24
Also from GRuB  you can try to choose recovery option and let it run through , then reboot.

Regards..

---

### Post by brunolabs on 2016-08-24
Hello.

It is an old desktop computer. Pentium 4. 2 GB RAM.
Ubuntu version 16.04.
This issue never happened before since version 7.04. Nor with other linux distros.

Do you need any extra information?

Thanks for helping.

---

### Post by ventrical on 2016-08-24
> **brunolabs said:**
> Hello.

It is an old desktop computer. Pentium 4. 2 GB RAM.
Ubuntu version 16.04.
This issue never happened before since version 7.04. Nor with other linux distros.

Do you need any extra information?

Thanks for helping.

Yes .. is it i386 (32bit) or amd64 bit?

Can you post results of 

```

lspci

```

from terminal ?

.. it may be the kernel upgrade blacklisted some older hardware.

Regards..

---

### Post by brunolabs on 2016-08-24
It is a 64 bit installation.

lspci output:
```
00:00.0 Host bridge: Silicon Integrated Systems [SiS] SiS649 Host (rev 10)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS965 [MuTIOL Media IO] (rev 48)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 IDE Controller (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] SiS7012 AC'97 Sound Controller (rev a0)
00:03.0 USB controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter
00:05.0 IDE interface: Silicon Integrated Systems [SiS] 182 SATA/RAID Controller (rev 01)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)
03:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV410 [Radeon X700]
03:00.1 Display controller: Advanced Micro Devices, Inc. [AMD/ATI] Device 5e6f
```


Thanks.

---

### Post by ventrical on 2016-08-24
It's a miracle you have that dinosaur running :)

 I assume it is graphics card. Could nomodeset installation perhaps help?

Regards..

---

### Post by Geoffrey_Arndt on 2016-08-24
This might sound like a silly question . . . BUT . . . instead of waking the PC from suspend/sleep by pressing any key or activating the track or mouse pad, have you tried pressing the "start button" _**firmly but briefly**_ . . . ??   In other words, not so long as to initiate a "hard boot".    On my various laptops, that IS the way they all wake up from suspend, . . . if suspend mode has been running for a few minutes.     Give it a try and let us know one way or another.    Apologies if you've already tried this.

---

### Post by T2uiYKb7 on 2016-08-25
Can you try pressing **" Alt+Ctrl+F1 "** ?

This happens to my Dad's computer and although the full desktop disappears he can still access those terminal screens.

If this is the case it's pretty easy to fix. (Maybe, I hope.)
[COLOR=#ff0000]
Edit: Sorry what I mean is press **" Alt+Ctrl+F1 " **while the screen is blank.[/COLOR]

---

### Post by brunolabs on 2016-08-25
Thank you in advance for your help.

> **Geoffrey_Arndt said:**
> This might sound like a silly question . . . BUT . . . instead of waking the PC from suspend/sleep by pressing any key or activating the track or mouse pad, have you tried pressing the "start button" _**firmly but briefly**_ . . . ??   In other words, not so long as to initiate a "hard boot".    On my various laptops, that IS the way they all wake up from suspend, . . . if suspend mode has been running for a few minutes.     Give it a try and let us know one way or another.    Apologies if you've already tried this.
Yes, I have already tried pressing the power button too but it didn't work. Most of the solutions I found online did not work for me. :(

> **andrew.nz said:**
> Can you try pressing **" Alt+Ctrl+F1 "** ?

This happens to my Dad's computer and although the full desktop disappears he can still access those terminal screens.

If this is the case it's pretty easy to fix. (Maybe, I hope.)
[COLOR=#ff0000]
Edit: Sorry what I mean is press **" Alt+Ctrl+F1 " **while the screen is blank.[/COLOR]
Alt+Ctrl+F1 works when I have the screen lock but only before the entering the sleep mode. After that it becomes completely unresponsive.


I guess I'll try the nomodeset installation suggested by ventrical.


Meanwhile, I realized this problem only happens after the first login. I mean, if the monitor goes to sleep mode before logging in the first time after a system reboot for example, the wake from sleep works correctly. Does this fact give you any more ideas?

---

### Post by brunolabs on 2016-08-25
Thank you in advance for your help.

> **Geoffrey_Arndt said:**
> This might sound like a silly question . . . BUT . . . instead of waking the PC from suspend/sleep by pressing any key or activating the track or mouse pad, have you tried pressing the "start button" _**firmly but briefly**_ . . . ??   In other words, not so long as to initiate a "hard boot".    On my various laptops, that IS the way they all wake up from suspend, . . . if suspend mode has been running for a few minutes.     Give it a try and let us know one way or another.    Apologies if you've already tried this.
Yes, I have already tried pressing the power button too but it didn't work. Most of the solutions I found online did not work for me. :(

> **andrew.nz said:**
> Can you try pressing **" Alt+Ctrl+F1 "** ?

This happens to my Dad's computer and although the full desktop disappears he can still access those terminal screens.

If this is the case it's pretty easy to fix. (Maybe, I hope.)
[COLOR=#ff0000]
Edit: Sorry what I mean is press **" Alt+Ctrl+F1 " **while the screen is blank.[/COLOR]
Alt+Ctrl+F1 works when I have the screen lock but only before the entering the sleep mode. After that it becomes completely unresponsive.


I guess I'll try the nomodeset installation suggested by ventrical.

Meanwhile, I realized this problem only happens after the first login. I mean, if the monitor goes to sleep mode before logging in the first time after a system reboot for example, the wake from sleep works correctly. Does this fact give you any more ideas?

---

### Post by T2uiYKb7 on 2016-08-25
In the past I've created a shortcut where when I press **Alt+M **it runs **xrandr --output HDMI1 --auto **and it turns the monitor back on.

You should be able to do the same to correct this problem (I guess it's more of a work around but it does just require press Alt+M when the screen goes blank.)

Can you open a terminal and type [COLOR=#006400]**xrandr**[/COLOR] and paste the results in here? It will list your monitor as **VGA1** , **LVDS1** , **HDMI1** or something along those lines.

---

### Post by brunolabs on 2016-08-26
> **andrew.nz said:**
> In the past I've created a shortcut where when I press **Alt+M **it runs **xrandr --output HDMI1 --auto **and it turns the monitor back on.

You should be able to do the same to correct this problem (I guess it's more of a work around but it does just require press Alt+M when the screen goes blank.)

Can you open a terminal and type [COLOR=#006400]**xrandr**[/COLOR] and paste the results in here? It will list your monitor as **VGA1** , **LVDS1** , **HDMI1** or something along those lines.

xrandr output:
```
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 4096 x 4096
VGA-0 connected primary 1280x1024+0+0 (normal left inverted right x axis y axis) 338mm x 270mm
   1280x1024     60.02*+  75.02  
   1152x864      75.00  
   1024x768      75.08    75.03    70.07    60.00  
   832x624       74.55  
   800x600       72.19    75.00    60.32    56.25  
   640x480       75.00    72.81    66.67    60.00  
   720x400       70.08  
S-video disconnected (normal left inverted right x axis y axis)
DVI-0 disconnected (normal left inverted right x axis y axis)
```

I'll try to replicate your command like "xrandr --output VGA-0 --auto"

Thanks. :)

---

### Post by T2uiYKb7 on 2016-08-26
Did that work?

When  it worked for me I think I still had access to the terminal screens. (Screen was blank until I press Alt+Ctrl+F1.)

---

### Post by brunolabs on 2016-08-26
No luck. :S
I validated the command in the terminal before adding the shortcut, but it did not work while the screen was locked.
The system becomes completely unresponsive. Also tried adding a new usb mouse during the screen lock, removing and connecting the VGA port, inserting a dvd, correctly entering the login password and then Enter (as the login screen was visible). The <Alt+Ctrl+F1> also has no effect in that state. Nothing seems to work.

I guess I'll open a bug report at Launchpad and use another distro for the moment. :(

Please post more possible solutions for this issue if you know any.


Thank you all for your help.

---

### Post by T2uiYKb7 on 2016-08-26
Oh OK so the entire system is unresponsive it's not a display issue.

Is going into sleep mode important do you need/want it?

You could try disabling all power management options or stop power management starting at all.

Then lock it manually and see if you have the same issue.

---

### Post by brunolabs on 2016-08-29
Still happens without automatic screen lock and power management. :\
I didn't find anyone else posting about this issue with such severity. I guess it has something to do with my old hardware.

Already opened bug at Launchpad. Let's see if anyone confirms it.


Thanks.

---

