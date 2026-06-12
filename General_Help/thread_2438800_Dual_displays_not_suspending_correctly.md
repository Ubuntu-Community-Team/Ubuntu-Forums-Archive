---
title: "Dual displays not suspending correctly"
date: 2020-03-18
forum: General Help
---

### Post by Gridwalker on 2020-03-18
I am having an issue with my monitors suspending correctly whilst my system is idle.

When my PC has been left idle, a number of things might happen when the system attempts to suspend the display :
[LIST=1]
[*]Most of the time, the display appears to suspend normally until the monitors lose signal, when the screens will reactivate and display the lock screen. The suspend countdown then restarts, and we enter into a loop.
[*]Occasionally, the display starts to suspend & fades to black with a visible mouse pointer. The monitors never lose signal, so the pointer remains on a blank screen until you move it. This most frequently happens if you lock the system before it attempts to suspend the display.
[*]Rarely, the system appears to suspend correctly, but has bands of distortion running across the left hand monitor when the system wakes. When moving items around on the right hand display, it seems that parts of that image are being corrupted and overlaid across the left hand screen. I have found no way of returning the left hand screen to normal, other than logging out or restarting GDM3.
[*]
[/LIST]
To be honest, I have no clue how to diagnose or resolve this. Any help will be appreciated!

---

### Post by sdsurfer on 2020-03-18
My first thought is that this is a display driver issue. For example, if your system is using some default display driver it "works" most of the time but there may be areas where the displays act up, like this. So first make sure that is in order.

It's a good idea to post the machine specs here, then in a terminal 
```
lspci |grep VGA
```

Using the information from that go into Search your Computer->System Settings->Software & Updates->Additional Drivers Tab, let it load, see if possibly it is using the generic noveau driver instead of your specific driver. 

This is all speculation without knowing the machine specs, but you might start by ensuring the graphics drivers are correct.

---

### Post by Gridwalker on 2020-03-18
The output to lspci |grep VGA is :
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Tahiti XT [Radeon HD 7970/8970 OEM / R9 280X]

The additional drivers tab does not even suggest a proprietary driver, as it has done on previous builds with older Nvidia cards ...

---

