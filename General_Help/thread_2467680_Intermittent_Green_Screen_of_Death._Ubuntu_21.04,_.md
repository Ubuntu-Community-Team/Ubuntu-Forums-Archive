---
title: "Intermittent Green Screen of Death. Ubuntu 21.04, AMD Ryzen 5 3400g"
date: 2021-10-04
forum: General Help
---

### Post by hisdudeness47 on 2021-10-04
Big issue here. Every couple days while working I get a seemingly random "Green Screen of Death". Green screen, locks up, SysReq Magic Key procedure doesn't work (I think). The only thing that works (so far) is powering off with the power button. Fires right back up when I start it again and behaves like nothing was wrong. The only thing I can think of that causes this is that this seems to happen when I'm under a heavy load (tons of Chrome windows, Telegram, Discord, Slack), but my CPU usage rarely ever goes over 60%. I also have 32 GB (4x8) of Corsair Vengeance LPX 3000 mhz RAM overclocked from the default levels of 2333 mhz to current levels of 2733 mhz (I haven't figured out yet how to get it higher). Unsure if RAM has anything to do with it, but it's underperforming spec, if anything. Not sure what's going on with this GSOD but I figured I'd share my specs. I'm at a complete loss for what to do/how to diagnose this issue as I'm relatively new to Linux/Ubuntu. My comp works great besides this. No other issues at all. Any thoughts on how to proceed?


**Specs in images below**



[LIST]
[*][inxi]("https://i.stack.imgur.com/1PDGT.png")
[*][dmidecode]("https://i.stack.imgur.com/LNtAD.png")
[*][About]("https://i.stack.imgur.com/mKbRX.png")
[/LIST]

**More system spec info**



[LIST]
[*]Ubuntu 21.04
[*]Gnome 3.38.5
[*]X11
[*]5.11.0-36-generic kernel
[*]AMD Ryzen 5 3400g
[*]Gigabyte B450 DS3H mobo
[/LIST]

[B]Other threads
[URL="https://askubuntu.com/questions/1367407/intermittent-green-screen-of-death-ubuntu-21-04-gnome-3-38-5-x11-5-11-0-36-g"]
AskUbuntu[/URL]
[Reddit]("https://www.reddit.com/r/Ubuntu/comments/q1b9bj/intermittent_green_screen_of_death_ubuntu_2104/?")
*******************************************************************************************
EDIT[/B]

Alright, I restored my UEFI optimized defaults and enabled XMP Profile 1 instead of manually OCing my ram, but it doesn't take. It's only running at 2133 mhz (same as default). This is why I did it manually in the first place. I don't understand. Should I manually boost voltage maybe? Thoughts on why the XMP profile doesn't do anything?


[After loading optimized default UEFI settings and enabling XMP Profile 1]("https://i.stack.imgur.com/sRXWf.png")

---

### Post by tea for one on 2021-10-04
> **hisdudeness47 said:**
>  SysReq Magic Key procedure doesn't work (I think)
Ubuntu does not ship with [COLOR="#0000FF"]REISUB[/COLOR] fully enabled.

It can be enabled by editing a system configuration file:-
```
sudo nano /etc/sysctl.d/10-magic-sysrq.conf
```
Then change the number in line 26 from 176 to 244 i.e. **kernel.sysrq = 244**

I found the solution at this site [https://digitalfortress.tech/debug/what-should-you-do-when-ubuntu-freezes/](https://digitalfortress.tech/debug/what-should-you-do-when-ubuntu-freezes/) and the information was in section 3.

By the way, the last letter in the process **B** reboots your system, sometimes you may want to power off completely by substituting the **B** for an **O**

---

### Post by hisdudeness47 on 2021-10-04
Hey, well that's good to know!! Thanks for that. That's strange that I never saw that issue in my days of REISUB research.

---

### Post by suuuunto on 2022-07-18
Any news here? I got the same problem :)

---

