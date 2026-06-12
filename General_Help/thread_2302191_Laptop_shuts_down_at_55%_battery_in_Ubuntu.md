---
title: "Laptop shuts down at 55% battery in Ubuntu"
date: 2015-11-08
forum: General Help
---

### Post by mistermagio on 2015-11-08
For some reason Ubuntu seems to think 55% is 'critically low' and shuts down the computer at that point. In the worst case scenario, it would be a hardware related problem (didn't have this issue in the past 2 years I've used this laptop though), but is there a way for me to find that out for sure, and if it is a software issue how would I fix it?

I can provide additionnal information if it is requested.

Edit: Solved, apparently. Just had to change a setting in dconf.

---

### Post by ajgreeny on 2015-11-08
Please tell everyone what the solution was in more detail, if you don't mind.

It will help other users in future who have the same problem.

---

### Post by mistermagio on 2015-11-08
Yes, I should do that, sorry. In dconf-editor, I had to go to:

 org => Gnome => settings-daemon => plugins => power and then change the value of the "use-time-for-policy" parameter from true to false, so that it would use the percentage based limits set in the same section instead of the time based ones. My guess is that in my case the issue was with a small hardware glitch making my computer think that the battery was about to run out when the 55% were crossed, and forcing the computer to look at the % left made things better. 

But in general I think using percentages would be more reliable than the default as well.

---

### Post by mistermagio on 2015-11-18
The problem appears to not be solved. I don't know why it managed to cross the 55% line just fine the other time, but it keeps rebooting when doing so now...

If anyone knows what could be wrong, it would help me a huge lot...

---

### Post by Vladlenin5000 on 2015-11-18
Well, batteries don't last forever, you know... And most manufacturers explicitly exclude it from their warranties. Some, like Dell in Europe offer a reduced (6 months) warranty coverage for the laptop batteries instead of the mandatory 24 months and that's perfectly legal in EU.

Laptop batteries are usually made for a 2-3 years lifespan at the most. Granted, in spite of that, some last longer 3 years with only a small reduction in capacity. However, most don't go past 2.5 years. It's time for you to check your, I would say.

---

### Post by mistermagio on 2015-11-18
But it really doesn't seem like 'natural' battery deterioration is at work here. When looking at battery stats, it seems that 44.4Wh remain out of the 50.6Wh it was supposed to have been shipped with (highest it has actually ever been was ~48Wh though). And it shuts down at 55% of the remaining 44.4Wh. Moreover, as previously mentionned, I have been able to pass that 55% mark and down to 40% (was testing it out) since the problem has appeared. Twice, even. 
I would add that I'm not the most demanding users on my laptop batteries, most of my use is done while the laptop is plugged in. I've crossed that 55% line 4 times since the issue has first appeared and it has been close to 2 months now. I know for sure that the issue is recent though, as in the entirety of my laptop's lifetime I went far below that line dozens of times without anything happening.

I don't rule out a problem with the hardware, obviously, but the issue is so weird that I still think it's possible (and likely) that there's a software issue here. 

If anyone has an idea of what my problem could be or needs any additional information, please ask.

---

### Post by tgalati4 on 2015-11-18
Battery packs are made of 3, 6, or 9 cells.  When one cell goes bad, the voltage drops very quickly.  The BIOS and power circuitry controls the emergency low-voltage shutdown, typically 10.5 Volts DC for a 12VDC battery.  You can watch the voltage by clicking on the battery icon, and look at the "Details" tab.

The battery will charge normally, but when the bad cell shuts down, it kills the entire battery pack with low voltage.  Time for a new battery.

---

### Post by mistermagio on 2015-11-18
Thanks for your answer, but I still don't understand how a bad cell would fully explains the issue, especially as since the issue has appeared I would have had to somehow bypass that bad cell problem twice. Would a cell gone bad possibly randomly ressurect like that sometimes? I'm genuinely wondering.

---

### Post by tgalati4 on 2015-11-18
Yes, a failing cell can sometimes hold voltage, and sometimes short out internally, causing low-voltage and the emergency shutdown condition.  Look at the voltages and watch what happens.  As the internal resistance of the battery increases, it causes a load on the battery pack, so there is not enough current to run the computer.  It's a common problem, with the only solution to replace the battery pack.  Battery packs are generally rated for 3 years or 300 cycles which ever happens first.

---

### Post by mistermagio on 2015-11-18
A shame then... Not even 2 years in and with less than 100 cycles. Just to know, would it actually be possible to watch the voltage when closing in on the line to actually confirm it, as the computer will shut down when the voltage drops?

I'll see with Asus about replacing the battery, I don't think I want to open that computer up myself...

---

### Post by tgalati4 on 2015-11-18
Well, you can watch it drop.  Install *acpitool* and post the following:

```
apcitool -B
```

Here's what a failing battery looks like:  (also Asus)

> tgalati4@Mint17 ~ $ acpitool -B 
  Battery #1     : present
    Remaining capacity : unknown, 97.59%
    Design capacity    : 4000 mA
    Last full capacity : 1201 mA, 30.02% of design capacity
    Capacity loss      : 69.98%
    Present rate       : 0 mA
    Charging state     : Unknown
    Battery type       : Li-ion 
    Model number       : GARDA71
    Serial number      : 1315


A failed battery is generally when capacity drops below 50%.

---

### Post by mistermagio on 2015-11-18
That's the reason why I didn't think my battery had a problem. Here's the output:

```
Battery #1     : present    Remaining capacity : 44189 mWh, 100.0%
    Design capacity    : 50616 mWh
    Last full capacity : 43722 mWh, 86.38% of design capacity
    Capacity loss      : 13.62%
    Present rate       : 0 mW
    Charging state     : Discharging
    Battery type       : Li-ion 
    Model number       : UX301-4

```

Still 86.4%, and it has barely gone down in the last few months (oscillates between 43.5 and 44.6 lately when fully charged). 
But I guess ACPI doesn't detect everything?

---

### Post by tgalati4 on 2015-11-18
It's possible that the sudden, emergency shutoffs fail to update the battery life records. 

If you have a power brick problem, then take out the battery and boot with just the AC cord.  Your system should stay up for several days.  If you have a sudden shutdown, then perhaps the power brick is bad.

If you have any cracks in the case, then perhaps you have a motherboard problem.

---

### Post by mistermagio on 2015-11-18
Well the computer works just fine as it is, it only shuts down when I have to use my computer unplugged long enough for it to go down to 55%. Afterwards if I plug it in again it will charge just fine and work just fine, until I go down to 55% again, etc. That really is the only issue, I don't think there's anything wrong with the motherboard or the power brick (I have 2 of them, too).

---

### Post by tgalati4 on 2015-11-18
Apply for a battery warranty.  Most manufacturers cover 80% capacity for 1 year.

---

