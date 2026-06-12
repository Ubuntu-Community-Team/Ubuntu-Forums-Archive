---
title: "Help with Flash Player. Slow when not in fullscreen. Settings greyed out."
date: 2015-09-27
forum: General Help
---

### Post by hey2 on 2015-09-27
Hi.

I just installed Ubuntu 14.04 on my desktop and i'm having some problems with flash player:

When flash player videos are not in full screen mode, they run really slow. I also noticed that the settings are grayed out in windowed mode, but in full screen everything is ok.

Does anybody know why is this happening?

Thank you.

---

### Post by claracc on 2015-09-27
It is important to know the hardware specifications of your system.
What is your graphics card?, Ram?, proccessor?
Do you have the same problem with all flash videos?

---

### Post by hey2 on 2015-09-27
> **claracc said:**
> It is important to know the hardware specifications of your system.
What is your graphics card?, Ram?, proccessor?
Do you have the same problem with all flash videos?

Hi.

Thank you very much for your reply.

It's a Pentium 4, 4gb ram (3.3 visible) and a HD3450.

Full screen runs very well but windowed it's slow. I also don't understand why the settings is grayed out unlike when it's in full screen.

The video are supposed to run slow or faster when full screen?

In my laptop the settings are visible in window mode.

---

### Post by ajgreeny on 2015-09-27
A Pentium 4, even with 4GB of memory, is going to find flash videos resource hungry, and with an AMD/ATI HD3450, which will be using the open source linux driver, you are going to find it difficult to get better performance, I'm afraid.

It is surprising, however, to hear that performance is better full screen than it is in a window.

---

### Post by hey2 on 2015-09-27
> **ajgreeny said:**
> A Pentium 4, even with 4GB of memory, is going to find flash videos resource hungry, and with an AMD/ATI HD3450, which will be using the open source linux driver, you are going to find it difficult to get better performance, I'm afraid.

It is surprising, however, to hear that performance is better full screen than it is in a window.

Hi

Thank for your reply.

What surprised me the most was the html5 performance. Unlike Windows XP, the videos are not choppy.

---

### Post by ajgreeny on 2015-09-27
I can't talk about Windows as I do not use it any more but certainly html5, though not very low in requirements, is not so resource hungry as flash in Linux, so that explains why html5 runs better than flash on you system.

---

### Post by hey2 on 2015-09-27
> **ajgreeny said:**
> I can't talk about Windows as I do not use it any more but certainly html5, though not very low in requirements, is not so resource hungry as flash in Linux, so that explains why html5 runs better than flash on you system.

Hi.

Yeas apparently it runs much better on Linux.

On XP it was really slow in Fullscreen.

Speaking of the flash issue, i just noticed something. If i zoom out the page where the flash video is running, it runs at normal speed. I don't know if it because it gets covered by the page, but it runs at normal speed.

Unfortunately since it gets covered it's unwatchable.

---

### Post by DK1993 on 2015-09-27
OP, do you happen to know if you are using the X.Org device wrapper for your video card or are you using ATI's proprietary driver? I would suggest heading over to ATI's website and installing the Catalyst driver and see if it improves your video performance with Flash.

---

### Post by hey2 on 2015-09-27
> **DK1993 said:**
> OP, do you happen to know if you are using the X.Org device wrapper for your video card or are you using ATI's proprietary driver? I would suggest heading over to ATI's website and installing the Catalyst driver and see if it improves your video performance with Flash.

Hi.

Thank you for your reply.

I posted this on another thread:

*-display               
       description: VGA compatible controller
       product: RV620 LE [Radeon HD 3450 AGP]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=64 mingnt=8
       resources: irq:16 memory:e0000000-efffffff ioport:c000(size=256) memory:fe9f0000-fe9fffff memory:fe9c0000-fe9dffff

---

### Post by DK1993 on 2015-09-27
OP, please go into terminal and type this in and paste the result (if any) in a reply ```
 fglrxinfo 
```

---

### Post by QIII on 2015-09-28
That GPU has not been supported by AMD's Linux driver for several years.  On going to "Additional Drivers", you would find that the fglrx driver is not offered.  Installing from AMD's website would more than likely end in disaster.

Don't attempt to install the fglrx driver.  You will need to keep using the default open source Radeon driver that was installed with Ubuntu.

---

### Post by hey2 on 2015-09-28
> **DK1993 said:**
> OP, please go into terminal and type this in and paste the result (if any) in a reply ```
 fglrxinfo 
```

Hi.

This message appear:

fglrxinfo: command not found

---

### Post by hey2 on 2015-09-28
> **QIII said:**
> That GPU has not been supported by AMD's Linux driver for several years.  On going to "Additional Drivers", you would find that the fglrx driver is not offered.  Installing from AMD's website would more than likely end in disaster.

Don't attempt to install the fglrx driver.  You will need to keep using the default open source Radeon driver that was installed with Ubuntu.

Hi.

Thanks for your answer.

I posted in another thread a problem that i have with the screen flashing when i click some things.

Do you think this could be a bug with the default driver and my card?

Thanks.

---

