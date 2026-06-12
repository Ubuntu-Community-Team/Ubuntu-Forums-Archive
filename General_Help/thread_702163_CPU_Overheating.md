---
title: "CPU Overheating"
date: 2008-02-20
forum: General Help
---

### Post by memyselfand on 2008-02-20
Hi everybody,

I have an Acer Aspire 3620 (more exactly Aspire 3623NWXCi) with Celeron M 1.5 GHz running Ubuntu 7.10 on Gnome and I've decided to install sensors-applet 1.7.12 as in gutsy repository. The problem is I'm getting 93ºC CPU temperature !!!  This happens when running Boinc using 90% of the CPU capacity. No overclocking, cpu fan appears to have no dust and is throwing a lot of (HOT) air. HDD temperature is 48ºC, and I have another heading "CPU TZS1" 30ºC which is probably a termometer attached to no chip, because my room's temperature is just a little less than that. The computer is not freezing (by no means you would say :D ) however and so far no warning messages or shutdowns or beeps.

I set up boinc to use 90% of the cpu, but the cpu is actually working at 100% all the time because linux and gnome needs 10% or more just to do "nothing".

When I set up boinc to use the default 60% of the cpu the temperature gets steady at 86ºC, when boinc is stoped CPU settles at 72ºC, which is still very high compared to other peoples computers...

My worries are that 1) Have my computer an emergency shutdown feature in case of overheating? I  couldn't find it on google, and the BIOS have no option for that and no temperature headings whatsoever...
2) Operating at high temperatures will make my computer less durable (I plan on staying with this computer at least more 1 1/2 years...

PS: 93ºC geee, I can almost boil water with my cpu...
Should I stop using boinc? It's such a nice program with a such noble cause...

---

### Post by BoeBoe on 2008-02-20
I think you can still use Boinc. Higher cpu usage will increase cpu clock and temperature by nature.
However I doubt the temperature reading accuracy from sensor applet since your BIOS does not provide any sensor link to interface temperature reading.

Usually when CPU overheat beyond limit, it will freeze or shutdown your system.
You can check the thermal grease bonding cpu & heatsink just to be sure.

---

### Post by phrawzty on 2008-02-20
> **BoeBoe said:**
> However I doubt the temperature reading accuracy from sensor applet since your BIOS does not provide any sensor link to interface temperature reading.

Most (all?) modern BIOS menus will have a way for you to view your system health sensors (fan speed, temperatures, etc..).  I would highly suggest reading through the documentation for your computer - specifically anything related to the BIOS - to see if it's something you either just haven't found yet, or needs to be enabled.

Assuming you can view your health sensors via BIOS at some point, it is worth comparing the idle temperatures reported directly by your BIOS with those reported by the sensor app in question.  Those figures seems *really* high, and i would be surprised if they were accurate...

---

### Post by memyselfand on 2008-02-20
I've checked carefully my BIOS and there's no temperature, voltage or fan speed headings. So I decided to install a temperature monitor on windows xp to see if I would get the same results. I've  first checked another computer of mine (an AMD desktop) which was at 57.5ºC at the BIOS. In windows software "Speedfan" the temperature however was 48ºC (go figure?) so I've decided to check with another software "MBM 5", with the same results. Then I installed speedfan on the laptop which all this is about. I'd like to add that I've checked the CD that Acer provides and there's no utility for such use.

Indeed, the temperature was very high also on window$: 81ºC cpu at idle state, the same 30ºC for the second thermal zone and 47ºC for my hd. There was only 3 voltages and no fan speed indicator (although I know the fan is smart because is varies among about 3 speeds plus inactive depending on the cpu temperature). One thing to note is that the cpu fan goes to full speed only at about 88ºC.

Doing some research I found that for various intel processors the maximum safe operational temperatures varies a lot from mere 60ºC to 100ºC:   [http://www.hardwaresecrets.com/article/143/5](http://www.hardwaresecrets.com/article/143/5)
I wanted to be sure for my specific processor so I found this intel datasheet [http://www.intel.com/design/mobile/datashts/303110.htm](http://www.intel.com/design/mobile/datashts/303110.htm)

What I read there made me astonished; It says there that in order to insure the long-term reliability of the processor (mine is chipset 370) the temperature of the cpu must not exceed 100ºC. It says also that if the Intel Thermal Monitor (inside the cpu die) is activated (recommended) the cpu clock will be lowered by hardware-means for a very small time just to maintain processor integrity and should not be noticed at all. However if this solution is not implemented (by the motherboard designer) or is disabled (no option in my BIOS) the cpu will force-shutdown when reach.....125ºC!!! Just to have clue last night the cpu was operating at some 91ºC when I burned my finger by touching the side of my laptop (where the hot air comes out), nothing serious though.

So, it seems I'm authorized to use the processor if it keeps below 100ºC. However I'm still concerned about the long-term reliability of my cpu, and don't know if I'll keep runing boinc at 90% or I will lower it to the default 60% (93ºC versus 86ºC last night)

---

