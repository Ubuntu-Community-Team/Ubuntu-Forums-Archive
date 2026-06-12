---
title: "Boot failed. ACCPI PCC proble failed"
date: 2015-08-20
forum: General Help
---

### Post by mfrp9 on 2015-08-20
Another one of these messages. While everyone on here is saying this is just a message, ubuntu should still load, the message can simply be ignored...it doesn't seem to let me ignore it. It gets stuck on this screen.

I attempted to boot into recovery mode as mentioned in another thread, but that didn't work out.

So I am getting this message, ubuntu seems to be stuck at this message and doesn't continue on with the boot, tips on troubleshooting?

---

### Post by mfrp9 on 2015-10-08
I have to bring this back up, as it comes back after installing security updates from 14.04. Any workarounds?

While I have no problems not upgrading, security updates seem serious enough to want to upgrade.

---

### Post by gordintoronto on 2015-10-09
If you edit the grub command to remove "quiet" I think you will find that it's getting past the "probe failed," and getting stuck later in the boot sequence.

---

### Post by mfrp9 on 2016-06-10
I hate to bring this back from the dead, but I'd like to be able to start updating my OS. Not sure where to go from here as most advice is to just "ignore" it. Is it possilbe hardware is not compatible with some of the kernels,driver,etc. that is being updated?

---

### Post by X-RED_Tech on 2016-06-10
Hardware specs?
Have you followed the advice given in the previous post? Results, I mean, were you able to find out where exactly it hangs? Yes, I have to reiterate that message has nothing to do with it.

---

### Post by grahammechanical on 2016-06-10
If the system is not loading to a desktop environment then upgrading to a newer version will not fix the problem. A fresh install might fix the problem. Please read the bug report and notice how people attach their problems to this message and will not accept that the cause of the message is not causing the problem they have.

[https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1432171](https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1432171)

That message does not appear in Ubuntu 16.04. What we do see is a message giving the result of a file system check (fsck) on the partition. Like the ACCPI PCC probe failed message the check is done early in the loading process and before the loading of a video driver. The video driver could be causing your problem.

Please start a new thread describing your actual problem and giving useful information about your system and set up. Are you running on a proprietary video driver? Have you changed video adapters?

We do not really know what your problem is but I doubt very much that it is related to that message.

Regards.

---

### Post by mfrp9 on 2016-06-15
The motherboard is L1N64-SLI WS ASUSTek Computer INC; CPU AMD Athlon 64 FX-74 Processor. I can post more information if you think it'd be helpful.

I'm not sure I know how to edit the grub command and turn off "quiet" mode so I have not done that.

---

### Post by mfrp9 on 2016-06-15
> **grahammechanical said:**
> If the system is not loading to a desktop environment then upgrading to a newer version will not fix the problem. A fresh install might fix the problem. Please read the bug report and notice how people attach their problems to this message and will not accept that the cause of the message is not causing the problem they have.

[https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1432171](https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1432171)

That message does not appear in Ubuntu 16.04. What we do see is a message giving the result of a file system check (fsck) on the partition. Like the ACCPI PCC probe failed message the check is done early in the loading process and before the loading of a video driver. The video driver could be causing your problem.

Please start a new thread describing your actual problem and giving useful information about your system and set up. Are you running on a proprietary video driver? Have you changed video adapters?

We do not really know what your problem is but I doubt very much that it is related to that message.

Regards.

Maybe I'm not making my issue clearer. I am not attempting to upgrade to a new version to fix the issue. A fresh install will always fix the problem. But after a few minutes on this fresh install, I will get new updates from Software Updater...when I update and restart my PC, it will not load and I will see the ACCPI message.

I can accept that this message may not be my problem, but this is the only indication I have that something different is happening after the updates are installed. I am on Ubuntu 14.04 and the info for my video card driver from running the lshw -c video command is below.

    *-display               
       description: VGA compatible controller
       product: Pitcairn PRO [Radeon HD 7850 / R7 265 / R9 270 1024SP]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:37 memory:a0000000-afffffff memory:bfdc0000-bfdfffff ioport:8800(size=256) memory:bfda0000-bfdbffff

---

### Post by X-RED_Tech on 2016-06-16
```
[COLOR=#000000]Pitcairn PRO [Radeon HD 7850 / R7 265 / R9 270 1024SP][/COLOR]
```

The above should work fine with the open source driver in 16.04.
In 14.04 it probably needs the proprietary drivers (fglrx).

---

