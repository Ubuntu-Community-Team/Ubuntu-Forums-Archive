---
title: "Overheating Laptop: Where's the /etc/module file?"
date: 2007-11-27
forum: General Help
---

### Post by i_like_you on 2007-11-27
I installed Gutsy on my Dell Inspiron 600M laptop a couple weeks ago. When I first tested it out with the Live Cd it made my laptop very hot. I figured this was due to it running off the cd and disregarded it as no big deal. But two weeks after performing a full install I still have this overheating problem. The laptop is always at least 50 degrees, even when idle (i know this because i run acpi -V in the terminal a lot and it's rarely below 50 degrees). But when I browse the web or listen to music or simply open up a text document the heat increases. It is especially bad when I'm watching a dvd or a video on youtube. If I don't keep the bottom of the laptop well-ventilated (the fan is on the bottom) the video will become choppy and unwatchable. To do anything even slightly intensive (like watching a video) takes up 80-100% of the cpu. And the laptop often reaches temperatures around 80 degrees.

I've been researching the problem. It's definitely an issue with Ubuntu. My fans are clean, thermal paste, etc. I had XP installed prior and it would only overheat when I was running a resource hog video game like Half-Life. But that was due to my crappy graphics card. I've heard a few people suggest editing the /etc/modules.conf file and pasting this in it:

battery
ac
thermal
processor
acpi-cpufreq
cpufreq-userspace

I can't find this file for the life of me. Was the name changed recently? I'd like to try this method out and see if it works. I would appreciate someone telling me how to access this inconspicuous file. Any other suggestions/advice would be welcome.

---

### Post by taurus on 2007-11-27
Maybe you mean /etc/modules?

```
gksudo gedit /etc/modules
```

---

### Post by i_like_you on 2007-11-27
Thank you! I added those lines to the file, saved it, and restarted the laptop.

But I still have the same problems. CPU is at 80-100% when watching  a You Tube video. The laptop temperature is presently 56 degrees, even though I'm doing nothing other than writing this post. The battery is fully charged, and should have at least an hour and a half to it. Instead it only gives me about 45 minutes. Any ideas of what else I could try?

---

