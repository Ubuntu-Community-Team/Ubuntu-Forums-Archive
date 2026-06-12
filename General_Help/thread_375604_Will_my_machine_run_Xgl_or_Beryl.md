---
title: "Will my machine run Xgl or Beryl?"
date: 2007-03-03
forum: General Help
---

### Post by darkenemy on 2007-03-03
i am running Ubuntu 6.10 with this machine
[http://pcdesktops.alege.net/Hewlett-Packard-Compaq-d530SFF-PB177USABA-PC-Desktop.html](http://pcdesktops.alege.net/Hewlett-Packard-Compaq-d530SFF-PB177USABA-PC-Desktop.html)
[http://www0.shopping.com/xPF-Presario-Desktop-with-AMD-AthlonT-XP-Processor-2900-SR1214NX](http://www0.shopping.com/xPF-Presario-Desktop-with-AMD-AthlonT-XP-Processor-2900-SR1214NX)
and i have been unsuccessful in installing Beryl or Xgl so far

i dont quite understand all of the logistics of using these programs
could someone just explain to me what these things are
Beryl
Xgl
Compiz
and what relationship all of these have with the Nvidia, Intell, or Ati cards (they are graphics cards right?)
why does it matter what card i have? do i not have a card that can run any of these?

if so, can anyone recommend a decent replacement that will work with my system and run everything cleanly? 

im fairly new to the whole linux thing and any help would be much appreciated.

---

### Post by darkenemy on 2007-03-03
i almost forgot, could someone also tell me what it means to have a "64bit" system, and if i have/should get one?  is it necessary to have a 64 bit system to run xgl, beryl, compiz, et cetera?

---

### Post by K.Mandla on 2007-03-04
[Beryl]("http://en.wikipedia.org/wiki/Beryl_%28window_manager%29"), [XGL]("http://en.wikipedia.org/wiki/Xgl") and [Compiz]("http://en.wikipedia.org/wiki/Compiz") are all roughly the same idea -- it's a desktop that is drawn with the assistance of the video card for enhanced visual effects.

As a result, what really determines if your machine can run any one of those three ... is the video card. Unfortunately, the system specs on those pages doesn't list the video card specifically, so you might have to figure it out on your own.

Type this into a terminal:

```
lspci -v
```
Hopefully, you should get some hardware information, including your video card. What you really want to see is Nvidia, ATI or Intel. From there you have a better idea of [how to install Beryl]("http://doc.gwos.org/index.php/BerylOnEdgy"), et al., and how well it will run.

As far as a [64-bit]("http://en.wikipedia.org/wiki/64-bit") system, I don't believe either machine you listed is 64-bit, but I might be wrong. I think Pentium 4 hyperthreading machines can handle 64-bit applications (someone correct me if I'm wrong), but are still [32-bit]("http://en.wikipedia.org/wiki/32-bit") machines. And if you had a 64-bit AMD system, it would be marked in big letters as a 64-bit machine. It's a braggable point. :)

It's not necessary to have a 64-bit machine to run Beryl, etc., because again, it depends mostly on the video card. It can run on some rather old machines, so long as the video card can handle the workload for it. So don't run out and buy a 64-bit machine just for Beryl. ;)

If you want more information about Beryl, or if you want to learn more about what machines will run it, you should ask on the [Beryl forums]("http://www.beryl-project.org/"). A lot of those folks use Ubuntu and can give you better tips on what works and what doesn't.

---

### Post by darkenemy on 2007-03-04
01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01) (prog-if 00 [VGA])
        Subsystem: ASUSTeK Computer Inc. Unknown device 8118
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 209
        Memory at e4000000 (32-bit, prefetchable) [size=64M]
        Memory at e8000000 (32-bit, non-prefetchable) [size=16M]
        [virtual] Expansion ROM at e9000000 [disabled] [size=64K]
        Capabilities: <access denied>

it says integrated video... so does that mean i dont even have a gfx card?
ill go over to the beryl folks and ask them.  thanx for the help

---

### Post by fsando on 2007-03-04
> **K.Mandla said:**
> From there you have a better idea of [how to install Beryl]("http://doc.gwos.org/index.php/BerylOnEdgy"), et al., and how well it will run.
From the link:
>  ATI
Radeon Driver
Ensure you have the open source radeon drivers installed. 
Do you know if the method also covers the x1600 card?

---

### Post by K.Mandla on 2007-03-05
> **darkenemy said:**
> 01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01) (prog-if 00 [VGA])
        Subsystem: ASUSTeK Computer Inc. Unknown device 8118
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 209
        Memory at e4000000 (32-bit, prefetchable) [size=64M]
        Memory at e8000000 (32-bit, non-prefetchable) [size=16M]
        [virtual] Expansion ROM at e9000000 [disabled] [size=64K]
        Capabilities: <access denied>

it says integrated video... so does that mean i dont even have a gfx card?
ill go over to the beryl folks and ask them.  thanx for the help
My pleasure. That message means you have an S3 video card that's built into your motherboard, and to be honest, I don't know if it can run Beryl or not.

> **fsando said:**
> Do you know if the method also covers the x1600 card?
I believe it does. However, I haven't used many ATI cards aside from a particularly quarrelsome 200m, so I don't dare pretend to know. :) Ask the Beryl forums for help. I'm sure they can tell you for certain.

---

### Post by fsando on 2007-03-05
I got it working now! Edgy+Beryl+Xgl+x1600
 I followed [[COLOR="Blue"]**_This guide_**[/COLOR]]("http://www.ubuntuforums.org/showthread.php?t=342812") by happis and it worked.
I've now disabled all beryl repos and am not going to change that until feisty.

---

