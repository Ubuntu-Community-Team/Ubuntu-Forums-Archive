---
title: "Live USB Doesn't Boot Past GRUB"
date: 2017-05-21
forum: General Help
---

### Post by SuperTeece on 2017-05-21
Greetings,

[COLOR="#FF0000"][SIZE=4]**tl;dr**[/SIZE][/COLOR] I can't boot my laptop from anything other than a Memtest86+ USB drive (all tests pass). Is there a verbose boot mode on the Ubuntu Live USB that might tell me what is failing?

*Details provided in the event someone has insight. I'm not asking for Windows troubleshooting :) *

**Core Specs:**
[LIST]
[*]Sager/Clevo P650SE
[*]Core i7 5700HQ
[*]32GB RAM
[*]2x 500GB SSDs - Raid 0
[*]1TB HDD
[/LIST]

**History:**
[LIST]
[*]Started with a BSOD for irql not equal to
[*]After reboot - about an hour later BSOD for kernel security check failure
[*]Neither BSOD mentioned a specific driver
[*]Time between BSODs shortened to approx 2 min
[*]Attempted booting into Safe Mode resulted in immediate BSOD with one of the two messages from above
[*]Within 2 hours of original BSOD the computer stopped booting into Windows entirely
[*]Now displays only black screen following POST
[*]Cannot boot to Windows USB Install Utility
[*]Cannot boot into Ubuntu live USB
[*]Displays GRUB menu - select Try Ubuntu - black screen
[/LIST]         

**Trouble Shooting Performed So Far:**
[LIST]
[*]Removed RAM
[*]Tried booting to Ubuntu USB with each stick - tried each stick in each slot
[*]Reflashed USB disk to check for corrupted flash
[*]Removed SSDs and HDD
[*]Tried RAM rotation again with Drives removed
[*]Reset BIOS by CMOS battery pull
[*]Visual inspection for physical damage or signs of over heat
[*]A single memory chip on one of the RAM sticks has a glossy appearance compared to the matte of the others - could be burned
[*]About a week before BSODs the computer did wake up in my backpack and bake for a few hours.
[*]Visual inspection revealed space between fan ducts and heat sink fins to be fairly clogged with gunk from the world
[/LIST]         

**Going Forward:**

I'm seeking more troubleshooting I may have missed. There is a lot out there for issues with OS not booting or USB sticks not booting but I cannot find a combination of the two.

---

### Post by gordintoronto on 2017-05-22
What version of Ubuntu? Have you tried the boot option, nomodeset?

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

It sounds like a motherboard problem which is probably beyond our power to fix.

---

### Post by SuperTeece on 2017-05-22
I'm trying 16.04.2 for the USB. No I have not tried that option but will after looking up what it does (never in too much of a rush to learn something new)

Yeah I fear the motherboard as well. The fact that memtest runs without issue gives me some hope.

---

### Post by SuperTeece on 2017-05-22
I just tried with nomodeset (not loading the graphics drivers was something I was wanting to try so thank you)

I also tried with removing quiet and splash to get the boot verbosity I was wanting.

In all cases the situation after GRUB is a black screen.

> **gordintoronto said:**
> What version of Ubuntu? Have you tried the boot option, nomodeset?

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

It sounds like a motherboard problem which is probably beyond our power to fix.

---

