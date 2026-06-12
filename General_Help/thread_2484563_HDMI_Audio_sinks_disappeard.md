---
title: "HDMI Audio sinks disappeard"
date: 2023-03-03
forum: General Help
---

### Post by detzi88 on 2023-03-03
Hi,
i had to switch the PCIe Port of my graphics card and since then, there are no HDMI Audio sinks listest anymore. (There were two). Video works fine, a Ubuntu LIve Picks it up fine, Windows does Pick it up fine. Only my existing install of Ubuntu 22.04 LTS does not recognize  them.
 - They are not listed in the settings Menue
 - Neither in the Pulse Audio Volume Control
 - Reinstalling Pulse Audio didn't help 
 - Rescanning also did not find any new devices
 - Fresh install of Ubuntu 22.04 LTS didn't help

I'm a bit at a loss here. Any Ideas?
Thanks
Detzi

---

### Post by JustSomeCanuck on 2023-03-03
That happened to me as well. I'm guessing that the latest set of updates broke something related to HDMI sound only, because my laptop's built-in speakers still work, as do headphones. Running the usual updates was the last thing I did before the problems started.

Do you see anything like this while your computer is booting? The last two lines only appeared for me yesterday:
[ATTACH=CONFIG]291857[/ATTACH]

---

### Post by DuckHook on 2023-03-04
Yep.

Ditto. Just after the latest upgrade. Websearch indicates that this is an old problem, so probably a regression. It happens.

I can't find the motivation to report this bug, upload my logs and do all the bisecting that the devs will want, so I'm going to wait for a future fix. 

I don't use the HDMI audio output, but I understand how frustrating this can be for those who do. If you do decide to start a bug report in Launchpad, I will add my "affects me too" vote to it if you link to the report on this thread.

---

### Post by detzi88 on 2023-03-04
So i tried a bit more stuff:
- Installed Fedora, does recognize
- installed 22.10 does in Live but not installed
- installed 22.04 LTS from a stick that is a few weeks old and i know worked before, without installing updates -> did not work
- reset my bios - no effect

> Do you see anything like this while your computer is booting? The last two lines only appeared for me yesterday:
No i haven't seen something like this. But i have a new Message there as well: "mtd device must be supplied (device name is empty)" i i think this is unrelated. [Bug report]([https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1981622](https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1981622))

I'm not quite sure if this is a regression. I have a USB Stick, a few weeks maybe months old, from which i know the HDMI devices were recognized after installing Ubuntu with it. So i used it to install 22.04 without checking "update during installation" which should have prevented any issue caused by updates. But on the other hand i have no idea what else it could be or what i should try.

---

### Post by DuckHook on 2023-03-04
I should know better than to assume that we share the same problem. My bad.
Please post the output of:```
journalctl -p 3 -xb
```

---

### Post by DuckHook on 2023-03-15
I hope the above forum members are still around to see this followup.

The 5.19.0-35 kernel contains a regression that nerfs the HDMI sound sink on almost all AMD graphics cards. The workaround is to use an older kernel at boot. If you have been keeping up with your updates, then that would be 5.19.0-32.

I got my HDMI back after using the older kernel.

You may wish to pin the -32 kernel and its associated libraries to stop the next update from automatically removing it.

Note that similar looking problems often have very different causes. If you are not using an AMD graphics card, then the cause of your problem is unrelated to this bug.

---

