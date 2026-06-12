---
title: "Frozen screen and odd lines on it"
date: 2015-01-05
forum: General Help
---

### Post by abelardopardo12 on 2015-01-05
Hi everyone,

I own a Dell Inspiron N4050 running with Ubuntu 12.04. It's been a while that my laptop's screen get frozen randomly. When it does, a lot of lines appear on the screen (as you can see on the photo). Does anyone know what is the problem and how could I troubleshoot it?

Thank you very much in advance!

---

### Post by poorguy on 2015-01-05
i had something very much like that in a windows desktop and it turned out that my graphics card driver didn't load so i rebooted and in my case it did fix it. being new to linux i don't know much about the drivers that are used but that is what i would look at first. is it that way on battery and ac power or just one or the other. does it change when you move the laptop lid any if it does it could be a cable proble and could also be from a cable being loose.  also i would check google and even the dell forums and see what you find. hope this helps and good luck.

poorguy

---

### Post by abelardopardo12 on 2015-01-06
@poorguy

Thank you very much for your answer and suggestions. I actually have my hard disk partitioned with a Ubuntu 12.04 OS and a Windows 7 OS. I noticed randomly frozen screens by using both OSs, but Ubuntu is the only OS where those odd lines appear. Answering your questons:

1. Is it that way on battery and ac power or just one or the other? **Both, either on battery and ac power**.
2. Does it change when you move the laptop lid? **It doesn't. My screen displays the same image with lines all the time while moving the laptop lid.**


What I did:
1. -On Windows- I reinstalled the graphic card driver (I downloaded it from the manufacturer website), but the problem hasn't been solved

---

### Post by Bucky Ball on 2015-01-06
Sounds like it is a hardware issue if you are getting screen issues on both OSs (particularly as you've re-installed the Win drivers and problem same in Win). Dead graphics card? How old is it?

---

### Post by abelardopardo12 on 2015-01-07
@Bucky Ball

I also thought about the same: a hardware issue!. But if it was a hardware issue, could I change the graphic card or it's embedded to the motherboard? Is there anyway to assure that's a hardware problem?. My laptop is fast 3 years old.

Thank you very much for your colaboration

---

### Post by Bucky Ball on 2015-01-07
> **abelardopardo12 said:**
> ... could I change the graphic card or it's embedded to the motherboard? 

Is it a card or part of the mother board? Perhaps open a terminal and give the result of this:

```
sudo lshw -C video
```

Post the output here, please.

> **abelardopardo12 said:**
> Thank you very much for your colaboration

It's a pleasure. Improvisation is a good thing and if I can't sort out your issue, we keep digging into it, someone might roll up who can! ;)

---

### Post by abelardopardo12 on 2015-01-09
After executing the command ```
sudo lshw -C video
```, I obtained the following results:


```
*-display               
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:43 memory:f6800000-f6bfffff memory:e0000000-efffffff ioport:f000(size=64)

```

---

### Post by poorguy on 2015-01-20
yeah hard call i have an hp / compaq and it gets the lock up frozen desktop no matter what distro i have tried to install from a dvd. what is strange i can run and install debian 7.7 now 7.8 from network install and it runs like a champ.

i have also had to install the propriatary tested driver to get graphics conflicts resolved also. from what i read linux really likes intel hardware. i have an old dell b110 desktop with all intel hardware and installed linux lite 2.2 on and it runs perfect no conlicts at all. 

good luck. the poorguy

---

