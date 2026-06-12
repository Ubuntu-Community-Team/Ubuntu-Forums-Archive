---
title: "Suggestion On New Computer Primarily For Ubuntu"
date: 2007-08-02
forum: General Help
---

### Post by boom2k1 on 2007-08-02
I bought a HP TX1220 notebook (HP's top of the line tablet PC) this month. I was really pissed because they haven't sent out a wifi replacement part in 3 weeks. Therefore, I am making my refund and going with the alternative.

My current alternative is to purchase the Asus EEE (for mobility) and a desktop (for home). I know it would probably save me half the money than keeping the HP TX1220.

I am going to build a new computer desktop for Ubuntu. I want to ensure that all the parts have maximum compatibility. I want to keep the budget low (< $500) but would need good specs for the next 4 years. 
-I already have a good 20" LCD screen, good logitech mouse, good speakers, and a good microsoft ergonomic keyboard 4000.

I would like you to suggest the model name of the parts and correct me if my assumptions are wrong?

I do programming and always work with large data.

I want:

cpu - Intel or AMD? (which model-- are there compatibility issues - I need a good bang for the buck ratio )
harddrive - 250GB+ (which model-is Seagate okay?)
motherboard - which brand? Asus???  which chip?
 - (I rarely do gaming, but I would need DVI out.) Do I need a graphics card, if so, which brand and model for maximum compatibility? 
RAM - 2GB - Does it really matter which brand I buy?
Ethernet Card - I think it will be included - which brand to avoid?
case - i would buy the cheapest
power - I don't know if it makes a difference

what else am I missing?

Thanks in advance!

---

### Post by stchman on 2007-08-02
> **boom2k1 said:**
> I bought a HP TX1220 notebook (HP's top of the line tablet PC) this month. I was really pissed because they haven't sent out a wifi replacement part in 3 weeks. Therefore, I am making my refund and going with the alternative.

My current alternative is to purchase the Asus EEE (for mobility) and a desktop (for home). I know it would probably save me half the money than keeping the HP TX1220.

I am going to build a new computer desktop for Ubuntu. I want to ensure that all the parts have maximum compatibility. I want to keep the budget low (< $500) but would need good specs for the next 4 years. 
-I already have a good 20" LCD screen, good logitech mouse, good speakers, and a good microsoft ergonomic keyboard 4000.

I would like you to suggest the model name of the parts and correct me if my assumptions are wrong?

I do programming and always work with large data.

I want:

cpu - Intel or AMD? (which model-- are there compatibility issues - I need a good bang for the buck ratio )
harddrive - 250GB+ (which model-is Seagate okay?)
motherboard - which brand? Asus???  which chip?
 - (I rarely do gaming, but I would need DVI out.) Do I need a graphics card, if so, which brand and model for maximum compatibility? 
RAM - 2GB - Does it really matter which brand I buy?
Ethernet Card - I think it will be included - which brand to avoid?
case - i would buy the cheapest
power - I don't know if it makes a difference

what else am I missing?

Thanks in advance!

Either Intel or AMD will work fine.
SATA or PATA hdds are fine
Stick with a name brand mobo
Buy decent RAM as this will give your system better stability
Most of your onboard ethernet cards are Nvidia or Realtek (both work)
Get a case that meets your needs
Buy a decent power supply
I recommend an Nvidia video card.
Onboard sound while functional is not as good as a PCI add in card (Go Audigy or Audigy 2)

---

### Post by w4ett on 2007-08-02
The previous poster's (stchman)  recommendations  are true...Two  Comments...Buy the best quality PSU you can afford on your budget and be sure to include plenty of case fans to dissipate heat.  60%-70%  of hardware failures can be attributed to heat buildup and Power Supply failure.

Additionally,  purchase a mobo that well supported by the manufacturer......You mentioned Asus...one of the big names, and a good choice.

---

### Post by boom2k1 on 2007-08-02
After some research, I found out 	Asus M2A-VM HDMI offers DVI interface and has 	Integrated Radeon X1250 (VGA, DVI-D, HDMi). 
Is the motherboard and this Integrated Radeon X1250 well supported?

Should I buy this motherboard instead of another motherboard and a graphics card?


As for RAM, I don't really understand what is good and what is not good!

THanks

---

### Post by Tyggna on 2007-08-02
I find that a single Intel Celeron 32bit can beat out an AMD 64 bit terion dual-core of the same clock speed.  For some reason, Ubuntu utilizes Intel chips better, and with that--a motherboard with an Intel chipset.

NVIDIA all the way - **NOT ATI**, I still can't get anything to work right on mine.  Don't need an SLI card, probably could cause problems.

Network card: 
   A: Wired:  Doesn't matter whatsoever.  Linux kicks butt with it.
   B: Wireless: Anything based on prism 2 drivers (D-link is pretty good about that)

RAM:  Linux will utilize any type or amount of RAM better than windows.  Windows has a very small memory leak (reboot about once a month to fix it), Ubuntu doesn't.

CompTIA says that for a power supply, you need to add 
10W for every 128Mgs of RAM
15W for your harddrive
30W for your motherboard
65+W for your CPU
10-20W for an optical drive 
5-10W for a Floppy
5-30W for PCMCIA and Adapter cards

Go from that, and depending on how fast your CPU, you might want to figure as high as 100W to be on the safe side, and stick with the higher-end suggestions.

One other thing:  My friend hasn't been able to get bluetooth working in Ubuntu--so you might want to avoid that feature.

---

### Post by upthelum on 2007-08-02
stchman was spot on. I use an asus A8V-VM-SE mobo which was only about 40 quid and has onboard vga which is fine so far and graphics ram can be allocated up to 256mb in bios. I got an athlon 64 from a friend which zips along fine in ubuntu and xp. Personally i would stay away from wireless networking but thats just my opinion. Hope this helps...

---

### Post by boom2k1 on 2007-08-02
Thanks!
if Asus M2A-VM HDMI doesn't work, I will go for

AMD with an Asus motherboard + NVIDIA card.
(i prefer AMD because I want something better than Pentium D but I don't want to get stuck with core 2 4300 .)

Is there anyone who bought an ASUS motherboard recently and have very good success with the chip?
Which model?
I guess I will be looking at the P5 series.

Thanks

---

### Post by w4ett on 2007-08-02
> **boom2k1 said:**
> Thanks!
if Asus M2A-VM HDMI doesn't work, I will go for

AMD with an Asus motherboard + NVIDIA card.
(i prefer AMD because I want something better than Pentium D but I don't want to get stuck with core 2 4300 .)

Is there anyone who bought an ASUS motherboard recently and have very good success with the chip?
Which model?
I guess I will be looking at the P5 series.

Thanks

The AMD and Nvidia combo will do well for you...I've always preferred AMD for some odd reason :o (except that since their purchase of ATI, the open sourcing of their drivers has been cr*p)....plus Nvidia support for Linux is good.  Memory wise, use the Mobo Mfg's recommendations.  Generic Memory, while it seems a cost savings initially, can cause problems in the long run.  Stick with Kingston, Apidia, Samsung are my recommendations.

---

