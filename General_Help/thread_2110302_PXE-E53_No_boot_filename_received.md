---
title: "PXE-E53: No boot filename received"
date: 2013-01-29
forum: General Help
---

### Post by brushman on 2013-01-29
I run only Ubuntu 11.10. Everything was working fine when one day, when I tried to log in, I got a black screen. I could type on the screen; I don't know if it was a command prompt or what, but I typed some random gibberish and hit enter. Pressed some buttons like escape and stuff to try to make something happen, and then resorted to holding the power button to turn the computer off. However, upon restarting, I got the following:

```
Intel(R) Boot Agent GE v1.3.65
Copyright (C) 1997-2010, Intel Corporation

CLIENT MAC ADDR: <removed> GUID: <removed>
PXE-E53: No boot filename received

PXE-M0F: Exiting Intel Boot Agent.

Reboot and Select proper Boot device
or Insert Boot Media in selected Boot device and press a key
```Note I removed my mac aaddr and guid because I don't know what those do so I don't know whether they're safe to post on the internet. I get this same message everytime I restart.

When I restart and go to the boot menu, I only have 2 options to select from:

IBA GE Slot 00C8 v1365
P4: HL-DT-ST DVDRAM GH24NS70

Neither work (I get the same message as above).

If at startup I go to the BIOS settings, and then over to the Boot subsection, I see: 

```
Boot Device Priority:                        <Optical Drives>
                                             <Hard Disk Drives>
                                             <Network>
                                             <Removable Drive>
Hard Drive Order                             No Hard Disk Drive
Optical Drive Order                          <P4: HL-DT-ST DVDRAM GH24>
Removable Drive Order                        No Removable Drive
<removed the rest as it seems unimportant>
```So my uneducated guess is that for some reason my computer no longer sees my harddrive. So what's going on? Help please! Thanks.

---

### Post by dcstar on 2013-01-30
> **brushman said:**
> 
..........
So my uneducated guess is that for some reason my computer no longer sees my harddrive.

Correct, you have a dead hard drive or a faulty motherboard/drive connection.

---

### Post by brushman on 2013-01-30
Would connecting an external hard drive give me any new information (like if the motherboard connection is faulty) or do external hard drives connect just like flash drives do?

---

### Post by brushman on 2013-02-01
I unplugged and replugged stuff, and now when I restart I get to the GRUB screen. However, when I select "Ubuntu, with Linux 3.0.0-24-generic" as usual, I get:

error : unkown command `linux'.
error: `hassum' is already loaded.

Pressing a key to continue brings me back to the GRUB screen, so I am unable to boot past this point.

---

### Post by dcstar on 2013-02-04
> **brushman said:**
> I unplugged and replugged stuff, and now when I restart I get to the GRUB screen. However, when I select "Ubuntu, with Linux 3.0.0-24-generic" as usual, I get:

error : unkown command `linux'.
error: `hassum' is already loaded.

Pressing a key to continue brings me back to the GRUB screen, so I am unable to boot past this point.

Boot the previous kernel, it is quite possible the drive is dying and the filesystem is corrupted.

---

### Post by brushman on 2013-02-06
hmm, now I don't even get to GRUB, before that I get

error: invalid arch independent ELF magic.
grub rescue>

---

