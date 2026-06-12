---
title: "Really weird installation issue with my hardware."
date: 2007-07-09
forum: General Help
---

### Post by Turboaaa2001 on 2007-07-09
This is both odd and annoying. I have a rig I built a while ago with an up-to-date BIOS and working hardware. It's running an AMD Sempron 3300+ with 768MB PC-2100 DDR RAM.

Let me start with a brief history on the rig:

1. I started with the CPU overclocked from 2200MHZ to 2530MHZ with a bad stick of 256MB PC-2100. I was running the system as a fileserver in command line only so I was using the "good" parts of the RAM until I could upgrade.

2. I just upgraded with putting brand new 512MB PC-2100 and a 256MB stick from a PC I was working on (Im a tech on the side) to bring it to 768MB. I then promptly broke the bad stick and placed it in the garbage.

3. I then took the heatsink out and cleaned the CPU and heatsink of the paste with Alchohal and removed dust from under the fan. After replacing everything and blowing dust out of the rest of the system I booted up. I did forget to plug the fan in and the CPU reached 120*  before I could shut it down.

4. After letting the system cool I booted up again with all fans working and temps at 42* w/ overclocking. I then attempted to boot off my HD into Ubuntu command line but got an error about continuis files.

5. I decided to re-install but every version (5.1, 6.06, 7.04, LinuxMint.Bianca, Red Hat 7.3, etx) I tried to install I kept getting an error about the kernel not liking the ACPI of the system.

I returned the BIOS to it's defualts and found that the overclocking was what caused the issue.

What I need to know is why? I have it running stock right now but I need it pushed higher to process data on the side. Here is some info on the CPU
 
The CPU has a fixed multiplyer of 11
The internal clock was increased from 200 to 230
The FSB was inscreased from 400 to 460MHZ

Can anyone explain this? Please help, this is a real inconvience......

---

### Post by Digitallysick on 2007-07-09
pc 2100?? why not pc 3200 or better? what are the stats on all your hardware

psu brand and voltage
processer
motherboard
etc

---

### Post by Turboaaa2001 on 2007-07-09
LOL I know what you mean. Have you seen the price diff between 2100 and 3200? I just called a bankrupt lawer for obvious reasons, so back when I could afford it I decided to skimp (not a good idea for overclocking I know. Bad TurboAAA)

My PSU is a 400w Antec
My MOBO is an EPoX with VIA chipset (I don't remember the actual model but the BIOS is updated)
Sempron 3300+ @ 2200MHZ stock (I want to run 2530MHZ)
Samsung 40GB HD
Seagate 300GB HD
Maxtor 300GB HD
Generic CD-ROM
Rage 128 PCI video

Right now I'm running 6.06LTS. I installed it running the CPU at stock frequency.

Just to repeat myself, this is my fileserver and it runs BOINC with several projects. I hope this helps, sorry I'm not more specific on the MOBO but I would have to dig out the rig from behind the entertainment center and I'm really tired right now:neutral:

If you want more info let me know.

---

### Post by Turboaaa2001 on 2007-07-10
Does anyone have any ideas?

Thanks,

---

