---
title: "Laptop sleeps periodically even while in use"
date: 2018-01-25
forum: General Help
---

### Post by sicklybeans on 2018-01-25
Apologies if this is posted in the wrong place, I'm a newb here. This is the only major bug I've encountered so far. 

**Bug Description: **Every 15 seconds or so, the computer display turns off and the screen locks even while I am actively using the computer. Note that this behavior is identical to what happens when I close and reopen my laptop.

**Bug Trigger: **When I reboot my computer the problem goes away until I close my laptop. Once I reopen my laptop, the problem persists until I restart the computer again. This means that I have to restart my computer every time I close my laptop because it becomes practically unusable.ThTh

**System specs**: 2017 Razer Blade laptop running a fresh install of Ubuntu 16.04.3 with Unity 7.4.0 (the default one). Nothing additional installed beyond the 3rd party drivers that automatically install. My settings are set to "Turn screen off after 5 minutes" and Lock is on.

**Additional Info**
After doing some testing, I have determined that the following **do not **trigger the bug:
 1. Typing "sudo pm-suspend"
 2. Typing "sudo pm-hibernate" (this does nothing on my computer)
 3. Locking the screen and then waiting for the screen to turn black

The only thing that seems to trigger the bug is physically closing the laptop and reopening it

Thanks!

---

### Post by sicklybeans on 2018-02-01
Bump/Update: I am now using Ubuntu Budgie remix 17.10 and this is still a problem so it's not unique to unity or 16.04. It's probably an issue with Razer Blade hardware

---

### Post by RobGoss on 2018-02-01
Have you checked your power setting to see if it's set correctly

---

### Post by sicklybeans on 2018-02-01
Im not sure exactly what you mean

---

### Post by RobGoss on 2018-02-01
> **sicklybeans said:**
> Im not sure exactly what you mean

There is a power management setting were you can select how you want your machine to behave, I always set mine to **never** that way my computer will not go into sleep mode every time I walk away from it

Try the **system settings**

---

### Post by sicklybeans on 2018-02-02
Oh, yeah I already did that and it didn't change anything

---

