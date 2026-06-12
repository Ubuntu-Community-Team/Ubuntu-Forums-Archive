---
title: "can't boot after new installation 18.04 Linux 5.3.0.40 kernel"
date: 2020-02-25
forum: General Help
---

### Post by An_Ngo on 2020-02-25
Hi:

I've been a happy Ubuntu user for about 15 years, that is why I rarely showed up in this forum.
Recently, my laptop shows some problematic behaviours, I guess that they are hardware problems, so I don't bother to fix them and just bought a new laptop.

I bought a HP 15ef0008ca 120 GB disk and 6GB . 
Right after the installation, after removing the usb stick, the laptop can't boot.
Nothing show up, but a black screen. 
I tried many times, most of the times, there was just a black screen. 
Sometimes, there were a lot of messages like 
"watchdog detected soft lockup on cpu 1,2,3,4 ....stuck 22s, 23s, 25s,....
"watchdog detected hard lockup on cpu 1,2,3,4" 
that went on forever... until I pushed the power button long enough to turn it off

I tried the "Advanced options ..."
Here I found the following options

Ubuntu, with Linux 5.3.0-40-generic 
Ubuntu, with Linux 5.3.0-40-generic (recovery mode)
Ubuntu, with Linux 5.0.0-23-generic
Ubuntu, with Linux 5.0.0-23-generic (recovery mode)

If I choose "Ubuntu, with Linux 5.3.0-40-generic (recovery mode)" and then just resume, it works but the screen looks very low quality. So, there might be some problems with the third party drivers for hardware with 5.3.30-40

If I choose "Ubuntu, with Linux 5.0.0-23-generic", it works OK. 

Now, it might be difficult to address the problem with third party drivers, so I would be happy if I can just boot into that "5.0.0-23" kernel.
Is there anyway to make that a default option? The laptop is used in a workplace, it not easy to ask all the users to remember to wait and make these choices instead of just turn it on.

Any help is highly appreciated.
Andy

---

### Post by wildmanne39 on 2020-02-25
*Thread moved to **General Help a more appropriate sub-forum**.*

---

### Post by An_Ngo on 2020-02-25
I found that I can make it boot into 5.0.0-23 by changing the file /etc/default/grub 
So, the problem is partly solved. 
However, if there is a way to address the problem with 5.3.0-40 I'd be happy to learn about.
Thank you very much
Andy

---

### Post by speartip on 2020-02-26
I too have had problems with the 5.3xxx Kernel, giving poor graphics performance & low Frames per second. The problem with the 5.0xxx Kernel is that it has now reached end of life. You would be better installing the 4.15xx Kernel which is supported for another 3 years by Ubuntu. Also have you checked in Driver Manager to see if it recommends any additional Graphics Driver?

---

### Post by rtb on 2020-02-27
I notice that your underlying hardware is AMD.  I've had similar problems on similar hardware, same kernel.  You may want to keep an eye on: [https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1863759](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1863759)

---

### Post by mörgæs on 2020-02-29
It would be great if you could test 20.04 in a live boot to see if the problems are fixed (and create a bug report if not).

---

### Post by jantroll on 2020-02-29
I have the same problem with every distro using 5.3.0-40 kernel (for example Mint).
My hardware is:
AMD Athlon 3000G
ASRock B450M-HDV R4.0 with R3.70 UEFI BIOS
8GB 3000MHz DDR4 RAM
240GB Crucial BX500 SSD

---

### Post by neonthunder on 2020-02-29
I've got pretty much the same problem

Thanks &#128522; so here's an update of what were currently running and how things look.

Gigabyte A320M-S2H - Micro ATX
PNY -128GB SDD
Corsair Vengeance LPX - 2 X 8GB
AMD Athlon 3000G

---

### Post by neonthunder on 2020-02-29
Just solved it by loading up with an earlier kernal :)

After booting up and working I restarted it and it's doing the exact same thing as before :(  unless I go to Ubuntu with Linux 5.3.0-28

---

