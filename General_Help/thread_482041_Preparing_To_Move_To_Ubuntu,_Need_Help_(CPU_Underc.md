---
title: "Preparing To Move To Ubuntu, Need Help (CPU Underclocking/Undervolting)"
date: 2007-06-23
forum: General Help
---

### Post by CompactDestruction on 2007-06-23
Hello, I've recently decided I want to switch from Windows XP to Ubuntu. I know some of the basics of Linux from experimenting with it before, e.g. I roughly know how to use a Terminal etc. My AMD64 iso image just finished downloading but there's a couple of things I need help with before I install.

My laptop is based on an MSI MS-1029 (also known as Megabook M635) chassis. It has the following hardware:

AMD Turion 64 MT-37
1024MB DDR333 RAM
128MB Ati Mobility Radeon X700
Realtek AC97 Audio
Inprocomm IPN2220 Wireless Chip

Presently I use RMClock in Windows to underclock and undervolt my CPU because it overheats otherwise. It can however sustain the length of an OS Install at the default clocks/volts.

So my questions are:

1. Is there an application for Linux that can interface with the processor in a similar manner to RMClock?

2. If not, is there a fairly simple method for specifying clock speeds and voltages to use?

I thank you all in advance for your help. If you need any more information please do not hesitate to ask. I'm happy to see everything that has been accomplished here and I hope to be a fully active member of your community when I get Ubuntu installed :)

---

### Post by CrispyFried on 2007-06-23
Im not sure about a linux util to do that but usually you can set those options in the bios. you wouldnt be able to change it on the fly though, it would stay at that speed/voltage till you change it again in the bios.

you might try running it in wine but Im not sure how wine would like something that goes so deep into the system.

---

### Post by mysticrider92 on 2007-06-23
There is a CPU frequency scaling applet for the GNOME desktop (and also the command line, I assume) that should allow you to lower the clock frequency if that is what you are looking for. 

Also, is there any paricular reason for the computer overheating? You might want to open it up and find out why (maybe put some Arctic Silver on the CPU to stop it from overheating, or get one of the laptop cooling pads.

---

### Post by CompactDestruction on 2007-06-23
This chassis seems to be overrated for the CPUs it can actually take. The cooling cannot cope with the processor. If I basically turn my MT-37 into an MT-34 and undervolt all is fine.

I've taken the lid off and there isn't a whole lot of dust in there.

If you can help me with my networking problem over in the other subforum I'll be ready to give Ubuntu a whirl.

---

### Post by CompactDestruction on 2007-06-23
> **mysticrider92 said:**
> There is a CPU frequency scaling applet for the GNOME desktop (and also the command line, I assume) that should allow you to lower the clock frequency if that is what you are looking for.

What is this utility called?

I am now in Ubuntu, with wireless fully on, with 3D Hardware Accelerated. I feel proud. It took some work but I am here :D

---

