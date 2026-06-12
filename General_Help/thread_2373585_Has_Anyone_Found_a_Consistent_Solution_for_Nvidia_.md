---
title: "Has Anyone Found a Consistent Solution for Nvidia 8400 GS?"
date: 2017-10-07
forum: General Help
---

### Post by sdsurfer on 2017-10-07
Error on startup: compiz crashed with signal 7 in malloc_consolidate(), Ubuntu 17.04, it is the Nvidia graphics driver/card. More details below.

I originally bought  this card for DND Forever a few years ago while I was still on Windows. It has always given me issues, and continues to do so in Ubuntu 17.04. After spending three (more) hours digging through search results, noting the same bug reports over and over on launchpad, I pose the question. I'm aware some of the latest drivers are worse, so I'm currently using 340.102.

In general the card and drivers "work," but consistently issues a compiz error on startup (details below.) The irony is I bought it for the two or three times a year I play games and nearly every high res game I try to run crashes at game start. HA! :-\

Aside, in those cases I tried running in lower resolution/architecture, still froze the game and sometimes the O.S.

I really don't think this is an OS problem. it is Nvidia, as said I've had issues with Windows as well.


Box: MSI board, AMD 64 architecture, Pentium dual core E5500, 2.80 Ghz, 4 GB RAM
Card Model: GeForce 8400GS
IRQ: 29
GPU UUID GPU-72042dba-750a-cc8d-f743-dc0da23594e6
Video BIOS: 70.18.6f.00.51
Bus Type:  PCIe
DMA Size:  40 bits
DMA Mask: 0xffffffffff
Bus Location: 0000:01:00.0


Some of what I think are the relevant details of the crash report:

ProblemType: Crash
Architecture: amd64
CurrentDesktop: Unity:Unity7
DistroRelease: Ubuntu 17.04
ExecutablePath: /usr/bin/compiz

(snip)

 NVIDIA Corporation GT218 [GeForce 8400 GS Rev. 3] [10de:10c3] (rev a2) (prog-if 00 [VGA controller])
   Subsystem: Device [196e:0877]
(snip)

proc.driver.nvidia.gpus.0000.01.00.0
- Error: [Errno 21] is a directory '/proc/driver/nvidia/gpus/0000:01:00.0'

*(note, the contents of that directory are two plain text files "information" and "registry", both of which I've examined but find nothing I can identify as aproblem)*

The rest all seems normal, no indication of problems I can see . . . thank you in advance for any ideas you may have.

---

### Post by Frogs Hair on 2017-10-07
I used that card without problems on number of Ubuntu releases with both the default and proprietary driver until replaced by a more powerful card. An 8400 GS is an entry level card and not a gaming card by current standards though it did work fairly well with a number of games when released .


> Overall, the Nvidia GeForce 8400 GS Rev. 3 has poor performance. This should be expected only from older dedicated graphics cards, so this graphics card should definitely be avoided if building a system to power modern applications and games. This graphics card is now over 7 years old, which means it is extremely out of date and is based on very aged technologies. The driver support for the Nvidia GeForce 8400 GS Rev. 3 is now fairly poor, so don't count on any new game optimizations. You may also encounter more and more graphical oddities as newer games are released.




---

### Post by Bashing-om on 2017-10-07
sdsurfer; Hello;

Note Frogs Hair's most excellent observations,

In addition might be good to insure there is no driver conflict at this time.
What shows :
```

dpkg -l | grep -i nvidia*
lsmod | grep -i nvidia

```

And what does X have to say about the situation ?
```

cat /var/log/Xorg.0.log

```

though -sometimes -
[INDENT][INDENT]we just got to move on
[/INDENT][/INDENT]

---

### Post by deadflowr on 2017-10-07
Probably less the card and more apport.
is there an actual issue or is it just spitting out the system has a problem popup?

---

### Post by Autodave on 2017-10-07
I am wondering how that would run on Xubuntu rather that Ubuntu w/Compiz running. With a 2.8 dual core and only 4 gig RAM, I would be trying something lighter. While that machine will never be a gaming rig, it should be half way decent.

---

### Post by sdsurfer on 2017-10-08
Thank you for your replies! Answers:

> . An 8400 GS is an entry level card and not a gaming card by current standards

At the time of the release of Duke Nukem Forever (which is ages ago, in Internet years) it was the recommended card. It has been a thorn in my side since but generally, works. As mentioned, gaming is infrequent for me, if it were just gaming issues I'd have never bothered to ask.

> What shows :

dpkg -l | grep -i nvidia*
ii  bbswitch-dkms                                               0.8-4ubuntu1                                  amd64        Interface for toggling the power on NVIDIA Optimus video cards
ii  libcuda1-340                                                340.102-0ubuntu3                              amd64        NVIDIA CUDA runtime library
ii  nvidia-340                                                  340.102-0ubuntu3                              amd64        NVIDIA binary driver - version 340.102
ii  nvidia-opencl-icd-340                                       340.102-0ubuntu3                              amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                                0.8.4                                         amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                                             367.35-0ubuntu1                               amd64        Tool for configuring the NVIDIA graphics driver


lsmod | grep -i nvidia
nvidia_uvm             36864  0
nvidia              10563584  66 nvidia_uvm
drm                   352256  3 nvidia


> And what does X have to say about the situation?

Its rather large, attached it, but I do see it claims some stuff about the CRT's not supporting Nvidia. I am guessing this just means it doesn't support the 3D stuff, etc, which I will never use. Briefly, monitor 1 an 2 are on a splitter, the second is the LG on a 25' cable to my painting table (watercolor artist) that is only on when I paint. The LG was was powered off when I ran this command. The first is actually a Dell, both 23" running at 1920 X 1080. Monitor two is a generic 17" at 1152 X 864, both on extended desktop.

> is there an actual issue or is it just spitting out the system has a problem popup? 

**Yes,** I am more concerned about the compiz error because it's a system complaint. I came across many threads indicating this is a bug and recommendations to disable it, but in this case it's pretty specific to this card so I can't call it that. I am a web developer by trade and in PHP/Perl/whatever, one of my gripes with some programmers is disabling warnings and errors, they are there for a reason and means you need to fix them. :-)

>  While that machine will never be a gaming rig, it should be half way decent.

Right, it's not a gaming console. I don't even do online matches, just a little bit of alien fracking from time to time. :-) My 8 core System76 lappie puts it to shame. I am not a "power user" when it comes to system demands, most of the time I run Netbeans, browsers, mail, etc. all concurrently and it's "good enough." As far as gaming, I've always checked the sys requirements before trying them out, but it's all down to the graphics and every one I've tried the 8x series GS is in their list.

Thank you all again for your replies, I am "newish" to home use of Ubuntu (three? four? months now) and I haven't been back in Windows since. This is a dual boot machine, Ubuntu on a 1 TB SSD, Windows on a 500GB SSD, third IDE for backups, all managed by grub.

---

### Post by Yellow Pasque on 2017-10-08
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1542967](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1542967)

I'm guessing compiz restarts and doesn't crash after startup? If so, it's probably not something to worry much about.

---

### Post by Frogs Hair on 2017-10-08
> [COLOR=#000000]At the time of the release of Duke Nukem Forever (which is ages ago, in Internet years) it was the recommended card. It has been a thorn in my side since but generally, works. As mentioned, gaming is infrequent for me, if it were just gaming issues I'd have never bothered to ask.[/COLOR]

The segment quoted in my post refers to applications as well. The main difference between the your system and mine at the time I was using an 8400 GS was the CPU. You're running a Pentium and I had a AMD 64 x II with the same speed rating. I last used that card with vanilla 16.04 though.

---

