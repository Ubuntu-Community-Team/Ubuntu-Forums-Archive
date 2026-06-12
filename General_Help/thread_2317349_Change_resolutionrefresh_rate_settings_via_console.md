---
title: "Change resolution/refresh rate settings via console (recovery mode)"
date: 2016-03-15
forum: General Help
---

### Post by lakeshore2985 on 2016-03-15
So I have a very old monitor which supports up to 1024x768@60hertz and am trying to connect to a Ubuntu box. Problem is I had used a full HD monitor while installing Ubuntu and now I get a black screen on the old monitor. How do I change/reset monitor settings on the console?

I managed to successfully changed monitor settings using the command "[COLOR=#222222][FONT=arial]xrandr --output VGA-0 --mode 1024x768 --rate 60", but it only works under Linux Mint, not Ubuntu. Also tried to "xrandr" while on recovery mode (Ubuntu) and the console gives an error message saying can't find display.[/FONT][/COLOR]

---

### Post by lakeshore2985 on 2016-03-17
Up!

---

### Post by papibe on 2016-03-17
Hi lakeshore2985.

Usually monitor resolution is not stored, unless you create a personalized Xorg config, or create personal settings using the a proprietary driver (Nvidia for example).

Do you have a Xorg config file? It is located in:
```
/etc/X11/xorg.conf
```
If so, try renaming it and boot again:
```
sudo mv -iv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```
If you use the Nvidia driver, also clean your personal settings:
```
rm -rf ~/.nv ~/.nvidia-settings-rc
```
I imagine the AMD driver may also save personal files, but I don't know the file names.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by him610 on 2016-03-17
The issue you describe happened to me several years ago. At the time, I was using the same monitor in a dual boot (WinXP & Ubuntu) machine, when using it in WinXP the graphics was set to the maximum setting then when rebooting to Linux there came a black screen.

My workaround was to set the graphics adapter/monitor to a lower resolution, ie 1024x768 before I exited WinXP. Afterwards when rebooting Linux, it proceeded to the login screen with no black screen. My own explanation was that it  seemed the previously set resolution 1024x768 left the system more in harmony with the capabilities of the hardware, drivers, and firmware/software.

On another occasion, I had just booted into a black screen then I got called upstairs by my spouse. When I returned about 15 minutes later the black screen was gone, replaced by the login screen. Does this indicate the logic in the xorg software keeps trying different resolutions until it finds a match? I don't know, but I never experienced the problem again.

---

### Post by lakeshore2985 on 2016-03-17
> **papibe said:**
> Hi lakeshore2985.

Usually monitor resolution is not stored, unless you create a personalized Xorg config, or create personal settings using the a proprietary driver (Nvidia for example).

Do you have a Xorg config file? It is located in:
```
/etc/X11/xorg.conf
```
If so, try renaming it and boot again:
```
sudo mv -iv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

No, I have no Xorg config file. What is it for? And why do I have to create one manually?

After creating a Xorg config file, what commands should I include? I just want to be able to change monitor settings via shell prompt on recovery mode so I can switch between different monitors.

---

