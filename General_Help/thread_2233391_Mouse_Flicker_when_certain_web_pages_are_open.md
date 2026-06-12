---
title: "Mouse Flicker when certain web pages are open"
date: 2014-07-08
forum: General Help
---

### Post by michael187 on 2014-07-08
When I have certain web pages open in either Chrome or FireFox the mouse will flicker to one degree or another. Pages that cause flicker are the posting section of this page and my schools forums. It's not very bad here but on my school pages it is very bad, almost unusable. The mouse will continue to flicker even when the web browser does not have focus. The only way to get it to stop flickering is to select a different tab or close the page. I've tried searching the internet and I do not have an unknown monitor and this: [FONT=Ubuntu Mono]gsettings set org.gnome.settings-daemon.plugins.cursor active false did not help either.

I am running 3 monitors, 2 off the AMD card and 1 off the Intel chip. There is no flicker on the Intel screen. I updated to the AMD drivers to resolve steam issues.

[/FONT]Ubuntu 14.04 LTS
CPU i5-4670K
Graphics Gallium 0.4 on AMD TAHITI (AMD drivers)
Intel on chip is using Linux drivers


michael@michael-desktop:~$ lspci |grep -i -E '(display|vga)'
00:02.0 Display controller: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller (rev 06)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Tahiti XT [Radeon HD 7970/8970 OEM / R9 280X]

If there is any-other information you need let me know.

---

### Post by michael187 on 2014-07-09
Bump for some help?

---

### Post by Garchomps on 2014-07-09
Go to Settings and then Displays. If you see any unknown monitors, disable them.

---

### Post by michael187 on 2014-07-11
> **Garchomps said:**
> Go to Settings and then Displays. If you see any unknown monitors, disable them.

No unknown monitors.

---

### Post by michael187 on 2014-07-12
I have solved the issue. It has to do with refresh rates of the screens. According to xrandr HDMI-0 was 1920x1080 60.0, DVI-0 was 1920x1080 60.0, and HDMI2 was 1440x900 59.9. I still have the occasional flicker on the screens being pushed by the ATI card but it is very reasonable now. To solve this issue I set the HDMI2 screen to a lower resolution 1280x960 60.0.

Additionally, I tried to create a newmode using cvt 1440 900 60.0 but it just ended up giving me a mode that was still 59.9 refresh. I'll look into this more latter and see if there is some where you can set the redraw rate of the mouse cursor.

---

### Post by Cleaver on 2015-06-21
OK, thanks! I definitely want 1080p on this monitor like it is now--I had the impression setting the resolution lower was a partial fix but created this thread due to my 1080p needs.

---

