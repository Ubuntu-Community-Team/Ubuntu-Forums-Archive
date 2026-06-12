---
title: "CPU scaling on X1E"
date: 2019-08-19
forum: General Help
---

### Post by eskubu2 on 2019-08-19
I'm running Ubuntu 19.04 (5.0.0-25-generic) on a ThinkPad-X1-Extreme (i7-8850H). I installed cpufreq gnome plugin to control cpu scaling. I created two custom profiles, one for AC (min/max frequency slider at 100%, 12 cores and boost enabled) and one for battery (min slider at 0%, max slider at 50%,12 cores and boost enabled) , the AC profile is the default profile and the battery profile is automatically selected via the tab "Power events". This worked perfectly: when AC is plugged in the freq is ~4ghz, when on battery it drops to ~2ghz. Now, when on battery it is sometimes required to get max speed so I used to switch the profile manually, in that case behavior on battery became the same as on AC: ~4ghz. 

Now, this appeared to  have stopped working. Apparently when switching to battery and selecting the AC profile, the cpu frequency drops to ~800Mhz when putting on load immediately. Also, in that case the widget no longer indicates the different cpu frequencies (it still indicates the overall frequency). To illustrate:

AC plugged in (sliders 100%), no load:

[ATTACH=CONFIG]283838[/ATTACH]

AC plugged in (sliders 100%), load via "stress --cpu 4":

[ATTACH=CONFIG]283839[/ATTACH]

While "stress --cpu 4" is still running, remove power cord. Immediately (like in 100msec) the frequency drops to 800Mhz. Note that the sliders are stlill at 100%. The widget also no longer indicates the individual cpu speeds, only the "overall" cpu speed on the top is working (when the widget is open it just stops refreshing the cpu speeds , it will still show the previous value. when restarting the widget it will simply show "--" like on the screenshot). 

[ATTACH=CONFIG]283840[/ATTACH]

From the moment the AC is plugged in, the widget will directly start showing the individual cpu speeds again and cpu freq will climb to 3.xx ghz like on the second screenshot

No idea what is going on, but it seems that something is overriding (?) the cpu speed when going to battery? Any idea what this could be or how to proceed in finding out what is going on?

---

### Post by DuckHook on 2019-08-19
I've never played with these tools and my input is of very limited value, but the power/battery/heat/cpu-freq interplay within Ubuntu is very complex and cross dependent. I'm not sure how the gnome plugin can override the pcmi subsystem that automagically sets cpu frequency to balance load, temp, stress and freq based on some arcane algorithm.

All I've ever done is allow Ubuntu to manage my power settings automagically for me, but then, my computing needs are simple and I've never wanted to overclock or otherwise fine tune my cpu.

Hopefully, someone more knowledgeable will be along shortly with their input.

---

### Post by eskubu2 on 2019-08-20
Thanks for your input. The CPU however is not overclocked, the gnome plugin simply allows to influence the scaling that happens when the system is idle. Fact is that by default the scaling is to aggressive on AC. On AC I'm using it as a workstation so I want no scaling at all. Thankfully this is still working. Afaik throttling will still happen automatically because of temperature but this is normal and unavoidable in case of such a laptop (I did undervolt to allow less throttling). On battery on the other hand I find the scaling to little. If I'm on battery I'm 90% of the time using it to read stuff and I want battery times to be at maximum so I force the scaling to maximum. So basically I want to disable all scaling when on AC and enable max scaling on battery and a way to dynamically chose between the two when needed, I don't want any smart algo deciding this for me. However, in some situations I do need max power on battery so I manually alter the scaling profile to "AC" but unfortunately if there is load the cpu appears to drop to 800mhz. I'm sure this behavior is new as it didn't do that before. Maybe this got broken because of updates that came in or something, I have no idea

---

