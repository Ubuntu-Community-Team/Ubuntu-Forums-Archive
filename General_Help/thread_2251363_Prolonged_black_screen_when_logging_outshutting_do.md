---
title: "Prolonged black screen when logging out/shutting down (plus other related issues)"
date: 2014-11-03
forum: General Help
---

### Post by billsmugs on 2014-11-03
I've installed Xubuntu 14.10 on my PC (dual boot with Windows 8) and I've got a series of small issues that appear to be connected. Xubuntu is running off an SSD and I have a fast processor and 16GB of RAM, so I would expect things to be quite fast, and they mostly are, except for the following situations:
[LIST]
[*]When logging out, my monitor immediately goes into "power save mode" and I get a black screen for ~10-20 seconds before seeing the login screen appear. After it has appeared I can log in normally (but typing during the blank screen phase doesn't result in any text having been entered when the display wakes up so it's not just that the screen is off).
[*]When shutting the computer down it takes quite a while to actually turn off. I assumed that this was the same issue, caused by the computer logging off, and getting stuck for a bit as above before shut down, but it even happens if I log off first, then shut down. Windows shuts down quickly without any trouble and the computer boots up quickly (few seconds) for either OS.
[*]If I lock the screen, I get the same prolonged black screen before seeing the password prompt appear. In this case though, entering my password gives me the black screen again for a bit, then kicks me back to the login prompt (I have to reboot to log back in).
[*]Attempting to switch to a terminal screen via Ctrl-Alt-F1 just stays on the black screen in power save mode until I Ctrl-Alt-F7 to get back to the desktop.
[/LIST]

Probably irrelevant, but including for completeness: while the monitor is in power save mode it makes a strange "wheeee-oooo" type sound in time with the flashing of the power LED (there are no speakers on the monitor, it's just a faint noise). I assume this is just the monitor and not anything to do with Xubuntu, but I've never noticed it before (e.g. while using sleep mode in Windows).

My personal hunch (I have very little past Linux experience, so I'm probably wrong) is that it's something to do with the graphics drivers, since I had trouble with them while installing Xubuntu (I have an Nvidia GTX980 graphics card which isn't supported by the open source Nouveau drivers, so I initially didn't get any video output while trying to install. I'm now using the official Nvidia drivers (ver. 343.22) and having no other graphics trouble).

---

### Post by billsmugs on 2014-11-08
Does anyone have any ideas on how to fix this? I've tried disabling light locker (which just stops me from locking the screen) and turning off "Handle display power management" in the Xfce Power Manager, but neither fix the problem.

---

### Post by billsmugs on 2014-11-10
I have now fixed this problem by adding a file "disable-nouveau.conf" to /etc/modprode.d containg the lines:
blacklist nouveau
options nouveau modeset=0

[FONT=Verdana](As described here: [/FONT][COLOR=#222222][FONT=Verdana]http://us.download.nvidia.com/XFree86/Linux-x86/343.22/README/commonproblems.html )

As well as adding the parameter "nomodeset" to the Ubuntu boot option in GRUB. The problem seemed to be caused by the Nouveau drivers interfering with the proper Nvidia drivers.[/FONT][/COLOR]

---

