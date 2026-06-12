---
title: "Hardware problems in Edgy and in Feisty"
date: 2007-03-18
forum: General Help
---

### Post by AdamBastard on 2007-03-18
[Edited apologetically after reading various posts, mostly by Aysiu, forum staff]
After days of searching, reading, and reconfiguring, I'm left with several unresolvable problems in my transition to Ubuntu, both in Edgy Eft and Feisty Fawn Herd 5. I'll present these issues and if anyone has an interest in looking into them or helping me figure out something, I will provide all requested information in hopes of improving this extremely good distribution.

I was able to set up a twinview configuration, and the NVidia Linux Driver Manual is pretty good. Still, I can't get a video overlay on my TV (i.e. videos played in Totem don't automatically pop up fullscreen on the TV) because **nvtv-out **doesn't work (fatal error: no compatible device found). Also, nobody that has posted in any forum *including* the nvtv project support forum has received more than "it's open source: program it yourself." I would if I knew how, are there any recommended resources to achieve this goal? I also lost the ability to "stick" windows to the desktop, which was really sweet. I don't know if that was a result of me installing Feisty or otherwise configuring the window manager, but if not, is there possibly a way to get this back?

Next problem. I have a 4.1 logitech speaker system with a Sound Blaster Live! oldschool soundcard. **ALSA-mixer **and volume control didn't pick up on it's existence on the first installation, but after disabling the onboard sound in BIOS and reinstalling the OS, it worked. I'm sure there was a file I could have reinstalled, but I had to redo the OS as a result of other tinkering anyway. The volume control in Gnome has a Master volume option, but in order to get the rear speakers working I had to adjust the Wave Surround volume. When I use the volume control on the keyboard, it can turn the Master volume up and down, where 'Master' refers only to the front speakers and sub, but not the rear speakers. I've done some exhaustive searches, and although I've read posts from people with the same problem, I haven't seen suggestions for solving the problem. Does this occur with all 4.1 systems, or is it card specific? Are there any files or websites that discuss the surround sound of the ALSA mixer and maybe how to link various volume controls to one another?

I am also using Logitech's S510 RF Keyboard/Mouse/Remote. The keyboard and mouse work, albeit at reduced functionality (does anyone know if any preconfigurations for other logitech keyboards work well with this model?), but the remote does nothing. I installed **LIRC** which apparently is used to control such devices, but I couldn't figure it out, and regardless of that, while following the instructions I received errors, possibly because the instructions were written for Edgy and I was by then using Feisty. Not that this common device is supported by LIRC anyway. A search on the internet will reveal pages of people saying "I'm not here to post a solution, I'm just in for the ride because I have the same problem." Clearly, if I use Ubuntu, I will not be using my remote. Argh. Unless, of course, there is a way to program the remote so that it sends keyboard-like commands to the computer, since the keyboard, mouse, and remote are all fed in through a single RF USB device. Any advice?

I want to setup an HP ScanJet 5300C too, if possible. I tried **XSane**, but it doesn't detect my scanner. Forums suggest I add myself to the 'scanner' group, which I did. It's being detected as a connect device... but most reports on the net indicate that this scanner only worked in dapper, and the avision driver has since not worked, a confirmed and unresolved issue. Are there any files that might be worth looking at, possibly to compare between Dapper and Edgy to see what was changed and how that might have affected the support for this device?

That's all, though. The software works very well, as does all hardware aside from that listed above (motherboard, hard drives, USB devices, printer, etc.). I know that all of these problems are a direct result of tragically poor support for multiple operating systems by the hardware vendors, including, of course, proprietary drivers that can't be ported to Linux. 

If anyone can point me in the right direction for TV-out, remote control drivers, scanner drivers, or master sound control that actually is master, I would be forever grateful and could then post the solutions for all to see. Even a single sentence might help, who knows.

Thank you,
Adam.

---

### Post by jethro10 on 2007-03-18
I am having the same problem with remotes it appears not to be Ubuntu or Feisty related.
Any linux kernel above 2.17 has remote functionality built in which is not quite the same as lirc and seems to conflict or interfere somehow.

Any other linux you may go to will have the same problem.

J

---

### Post by AdamBastard on 2007-03-18
Haha, that's exactly the kind of post I was referring to indeed. 
You're right though, I should have stated "Clearly, if I use ***Linux***, I will not be using my remote. Argh." :-D

It's frustrating to buy hardware when, down the road, you are extorted. Either buy the OS that supports it, or buy the hardware supported by the free OS and garbage the stuff you already purchased. Makes me wish I was in Computer Science, and not Psychology.

---

### Post by AdamBastard on 2007-03-19
[Aysiu]("http://www.ubuntuforums.org/member.php?u=21941") is very extremely smart. Learning linux after windows is like learning a new language, and it is easy to forget how much time and energy went into getting the first one down. Thanks. :)

---

### Post by jethro10 on 2007-03-22
> **AdamBastard said:**
> 
It's frustrating to buy hardware when, down the road, you are extorted. Either buy the OS that supports it, or buy the hardware supported by the free OS and garbage the stuff you already purchased. Makes me wish I was in Computer Science, and not Psychology.

Thats exactly what i've started to do, buy mainstream hardware eg HP printers, Canon lide scanners because they just work on Linux.

It'll take a while though.
J

---

### Post by AdamBastard on 2007-03-24
Very true. Fortunately, I have a laptop as well that doesn't have tons of random hardware connected to it, and it works extremely well with just Ubuntu on it (Windows was too slow and useless). The sound broke somehow, but that's the kind of thing that can be fixed eventually, plus I normally have to keep the sound off anyway. 

Anyway, thanks for your replies Jethro!

---

