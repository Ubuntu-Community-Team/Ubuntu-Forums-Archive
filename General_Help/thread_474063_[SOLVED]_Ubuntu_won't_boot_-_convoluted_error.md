---
title: "[SOLVED] Ubuntu won't boot - convoluted error"
date: 2007-06-14
forum: General Help
---

### Post by altonbr on 2007-06-14
After Grub initializes and gives you the 2 second window to hit 'esc', a message says "Loading Up...", flashes twice, and then gives this error:

```
Int: 14 CR2 df800000 err 00000000 EIP c020c384 CS 00000060 flags 00010007
Stack: c00f8050 c03f71d8c 00000002 c00f8059 000f8050 00000000 00000000
```I thought this looked like a memory dump, so I ran memtest86+ - which I was able to get to and run from the Grub menu (so therefore v1.65) - for 24 hours. The 512MB memory module contains no errors.

Rough specs on Compaq Presario SR1224NX are:[LIST]
[*] **Operating System:** Ubuntu Feisty 7.04 - fresh install
[*] **Motherboard:** Micro-Star Gamila/Giovani/Neon series, 030[LIST]
[*]**BIOS:** Phoenix Tech. 3.15 (2004-08-05)
[*]**FSB:** 400Mhz[/LIST] 
[*] **Processor:** Pentium 4 2.8GHz (130nm)[LIST]
[*]**L1:** 12kB/16kB
[*]**L2:** 512kB
[*]**Core:** Northwood
[*]**Socket:** 478[/LIST] 
[*] **Chipset/Video Card:** Intel i845G rev. B1
[*] **RAM:** ???[LIST]
[*]**Size:** 512MB
[*]**Type:** DDR 3200
[*]**Timing:** 2.5-2-2-6[/LIST] 
[*]**Hard Drive:** ???[/LIST]This is Compaq's specifications: [http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&lang=en&cc=us&product=441131&dlc=en&docname=c00146969](http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&lang=en&cc=us&product=441131&dlc=en&docname=c00146969)

This is my cousin's computer who's been running a fresh install of 7.04 for about 3 weeks now. She's had no problems until she turned the computer off by the main power button and not via the GUI. I'm not here to say what obviously went wrong, I'm just wondering if someone can help fix it.

I will boot into a LiveCD right now and try to back up her documents.
[U][SIZE=4]
**** RESOLVED ****[/SIZE][/U]
Add the flag '**acpi=off**' to the kernel line in Grub before booting up.

To do so, follow these instructions when the computer is booting up:
[LIST=1]
[*]hit '_esc_' while Grub is loading (multiple times because you only have a 2 second window)[LIST=1]
[*]it should now show a list of kernels[/LIST]
[*]find your newest kernel that doesn't say '*(recovery mode)*'  and hit '_e_' (for edit)
[*]find the line that begins with '*kernel*' and hit '_e_' again
[*]at the end of the '*kernel*' line, remove '*quiet*' (for debugging purposes) and concatenate '***acpi=off***'[LIST=1]
[*]then hit '_esc_' when you're finished[/LIST]
[*]hit '_b_' to boot the specific kernel you just edited
[*]if it boots successfully and you can open a terminal, type 'sudo vi /boot/grub/menu.lst' and add '*acpi=off*' to every 'kernel' line that you will boot from. You don't have to erase 'quiet' this time, because there is no point in debugging the boot sequence once the problem is solved[/LIST] Here is an example:
```
title           Ubuntu, kernel 2.6.20-16-386
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.20-16-386 root=UUID=9c978d7a-bd4a-4394-a093-9db0d39ab5ce ro quiet splash **acpi=off**
initrd          /boot/initrd.img-2.6.20-16-386
savedefault

```Hope this helps!

---

### Post by logos34 on 2007-06-14
> She's had no problems until she turned the computer off by the main power button and not via the GUI.

Not a very smart move.  Now she's got data and/or filesystem corruption.  

From the live CD I'd run **sudo fsck /dev/hda1**  (or hda2, etc, whatever your root partition is).

---

### Post by Crafty Kisses on 2007-06-14
> **logos34 said:**
> Not a very smart move.  Now she's got data and/or filesystem corruption.  

From the live CD I'd run **sudo fsck /dev/hda1**  (or hda2, etc, whatever your root partition is).

Sorry, had to comment, that's the funniest post all day. :KS

---

### Post by mdurham on 2007-06-14
> **Codename said:**
> Sorry, had to comment, that's the funniest post all day. :KS

I don't get it. What's the joke that you are talking about?

---

### Post by altonbr on 2007-06-14
> **logos34 said:**
> Not a very smart move.  Now she's got data and/or filesystem corruption.  

From the live CD I'd run **sudo fsck /dev/hda1**  (or hda2, etc, whatever your root partition is).

Thanks for the info, I'll try that out.

I knew it was a stupid move, hense why I said this:

> **altonbr said:**
> I'm not here to say what obviously went wrong, I'm just wondering if someone can help fix it.

I'm just surprised because I've seen Ubuntu recover from every single power outage I've seen. I personally have 1 UPS per computer, but others usually don't invest in such a device.

---

### Post by logos34 on 2007-06-14
> I'm just surprised because I've seen Ubuntu recover from every single power outage I've seen. I personally have 1 UPS per computer, but others usually don't invest in such a device.

Yeah, ext3 is basically journalised ext2 so it's pretty resilient...I had one power outage and I had errors upon restart, but fsck detected and repaired them.

---

### Post by altonbr on 2007-06-14
That's not good, the same error appears when I put in the LiveCD... Maybe she's a pathological liar and picked it up and dropped it for fun... which would also mean she's something else - I forget what it's called...

I'll unplug and replug the cords on the mobo.

This worries me though because the LiveCD doesn't talk to the hard drive... I wonder if it's a CPU problem. I've almost covered everything else...

---

### Post by altonbr on 2007-06-14
I took everything apart except for the mobo off the tower and the power supply, then put it all back together, and no luck :S

Any ideas?

(Sorry, it doesn't seem like this is a Ubuntu problem anymore, but I'm sure a lot of you build your own systems)

---

### Post by logos34 on 2007-06-15
> (Sorry, it doesn't seem like this is a Ubuntu problem anymore, but I'm sure a lot of you build your own systems)

No, it looks like a hardware issue.  Sorry to hear that.

I've only built a couple of fairly basic desktop systems and about the only hardware troubleshooting I've had to do involved tracking down a booting problem last summer, the cause of which I traced to a failing power supply.  (I thought for sure it was the motherboard at first).  But if I were you I'd start with the hard drive again by taking it out and connecting it to another computer and seeing if you can access the data on it (not boot it).  If may be physically damaged...S.M.A.R.T diagnostic will tell you more about that.  Try swapping out the power supply if possible.  You've ruled out the memory.  Check the cpu and mobo next.  

Good luck.

---

### Post by altonbr on 2007-06-15
Thanks for your help logos, I'll read my Scott Mueller book on Updrading and Repairing PCs to see if I can find that error message in there;  If I can least find WHAT is sending that signal, then I'm golden.

Any other ideas while I'm at it?

---

### Post by altonbr on 2007-06-15
Huh.

It now seems to be able to boot from the Feisty LiveCD when I change the boot options by deleting 'quiet' (for debugging purposes) and adding in '**acpi=off**'. I've had many problems with acpi in the past (on older computers), but never on this one as far as I can recall.

I'll tell you how it goes.

---

### Post by altonbr on 2007-06-15
Yup, it was an acpi error. This thread is resolved.

Thanks everyone for your help.

Grub will simply copy the flags I edited in the boot line in /boot/grub/menu.lst when it upgrades to a new kernel, won't it?

---

