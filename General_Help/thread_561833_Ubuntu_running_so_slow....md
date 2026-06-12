---
title: "Ubuntu running so slow..."
date: 2007-09-28
forum: General Help
---

### Post by gimsys on 2007-09-28
Hello :)

I've just installed ubntu and it's running kinda slow for my machine, windows runs much faster

Here is my system configuration:
Processor: Intel Pentium 4 3000 Mhz  Hyper Threading
Memory: 1 GB DDR 400 dual chanel
Video: Ge Force FX 5200 128MB
Motherboard: Asus P4C800 deluxe
Harddisks: Western digital 80 GB IDE
                  Western Digital 160 GB IDE
                  Seagate 160 GB SATA
DVD-RW ASus

Is there a way to make it run faster or that it's just the way it runs  ?
I had some problems when I installed it , i had to stop enhanced mode on PATA so i can boot ubuntu

My Unbuntu is installed on the second partition on the 160GB western digital , which was purchased this year  few months ago

Thanks in advance :)

---

### Post by gimsys on 2007-09-28
please !:confused:

---

### Post by amo-ej1 on 2007-09-28
Well you need to identify some bottlenecks on your system. Try to measure the harddisk throughput you got on all harddisk (man hdparm) look at the top (man top) output and see what's blocking, is there much I/O, what's the CPU doing ?, how much memory is used ? 

Start by defining _what_ is going slow, if you graphical environment is slow, then do you have the accelerated video drivers (e.g. in case of an nvidia video card) installed ?

---

