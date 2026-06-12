---
title: "Sounds repeat after an incoming phone call"
date: 2007-06-24
forum: General Help
---

### Post by Whydoe on 2007-06-24
Normally I would search for this problem - but it's just too quirky.   I'm using a ESS 56 K modem and a SB Live! sound card with Feisty.  Everything works fine till I get an incoming phone call.  For whatever reason, all the sounds on the computer skip/repeat after the phone rings.  Also, I cannot dialup to the internet unless I reboot the system.  It just hangs just after dialing - it doesn't get to the login prompt.  I'm thinking it's either BIOS or an IRQ setting but I can't tell.  
Any thoughts?  There probably is a solution to this on here somewhere I've missed.  

Pentium III 600, 400MB, Geforce2 Ti, Feisty, SB Live!, 56 Dailup Modem.

---

### Post by shssta on 2007-06-26
im having a similar problem, do you also get an error message in the terminal about it disabling irq# 10?

---

### Post by Whydoe on 2007-06-26
I don't get any errors - but then I didn't check in the terminal.  How did you bring up the error in the terminal?  I think maybe the modem is set in the BIOS to do some sort of function when the modem gets an incoming call.  I'll check the terminal next time and see what happens.

---

### Post by Whydoe on 2007-06-28
I've just found out by using...

lspci -v

that both my sound card and modem share the same IRQ (4).  This is part of the output.

> 00:09.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)
        Subsystem: Creative Labs SBLive! 5.1 Digital Model SB0220
        Flags: bus master, medium devsel, latency 32, IRQ 4
        I/O ports at d000 [size=32]
        Capabilities: <access denied>
00:0d.0 Communication controller: ESS Technology ES2898 Modem (rev 02)
        Flags: fast devsel, IRQ 4
        I/O ports at b400 [size=8]
        Capabilities: <access denied>


What way do I have to change the IRQs on these items without causing conflicts?

---

### Post by Whydoe on 2008-05-21
Just started using Ubuntu Hardy and I'm still having this problem.  If I get an incoming call, the computer responds "choppy" mouse moves around slowly and the sound reacts the same.  The only difference is that now the sound card and modem share IRQ 5.  It is a fresh install of Hardy.

---

### Post by Whydoe on 2008-05-23
So, this is the output I get in the kernel.log (in the System Log) after I get an incoming call.  

May 23 18:05:03 ****-desktop kernel: [ 2034.307218]  [__report_bad_irq+0x24/0x80] __report_bad_irq+0x24/0x80 
May 23 18:05:03 ****-desktop kernel: [ 2034.307246]  [note_interrupt+0x27b/0x2c0] note_interrupt+0x27b/0x2c0 
May 23 18:05:03 ****-desktop kernel: [ 2034.307276]  [handle_IRQ_event+0x30/0x60] handle_IRQ_event+0x30/0x60 
May 23 18:05:03 ****-desktop kernel: [ 2034.307311]  [handle_level_irq+0x91/0xf0] handle_level_irq+0x91/0xf0 
May 23 18:05:03 ****-desktop kernel: [ 2034.307334]  [do_IRQ+0x3b/0x70] do_IRQ+0x3b/0x70 
May 23 18:05:03 ****-desktop kernel: [ 2034.307370]  [common_interrupt+0x23/0x30] common_interrupt+0x23/0x30 
May 23 18:05:03 ****-desktop kernel: [ 2034.307410]  [__do_softirq+0x61/0x110] __do_softirq+0x61/0x110 
May 23 18:05:03 ****-desktop kernel: [ 2034.307451]  [do_softirq+0x55/0x60] do_softirq+0x55/0x60 
May 23 18:05:03 ****-desktop kernel: [ 2034.307465]  [irq_exit+0x6d/0x80] irq_exit+0x6d/0x80 
May 23 18:05:03 ****-desktop kernel: [ 2034.307476]  [do_IRQ+0x40/0x70] do_IRQ+0x40/0x70 
May 23 18:05:03 ****-desktop kernel: [ 2034.307505]  [common_interrupt+0x23/0x30] common_interrupt+0x23/0x30 
May 23 18:05:03 ****-desktop kernel: [ 2034.307562]  ======================= 
May 23 18:05:03 ****-desktop kernel: [ 2034.307567] handlers: 
May 23 18:05:03 ****-desktop kernel: [ 2034.307572] [<d88e4b80>] (usb_hcd_irq+0x0/0x60 [usbcore]) 
May 23 18:05:03 ****-desktop kernel: [ 2034.307679] [<d8b78b60>] (snd_emu10k1_interrupt+0x0/0x540 [snd_emu10k1]) 
May 23 18:05:03 ****-desktop kernel: [ 2034.307740] Disabling IRQ #5

Any ideas yet?

---

### Post by Whydoe on 2008-05-25
Okay, sound like a unique problem... but anyway, I fixed the sound issue by moving the sound card to another PCI slot, but I still get choppy response from mouse.  This is the output from lspci -v now...

00:04.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 11) (prog-if 00 [UHCI])
	Subsystem: First International Computer, Inc. VA-502 Mainboard
	Flags: bus master, medium devsel, latency 32, IRQ 3
	I/O ports at d400 [size=32]

00:0d.0 Communication controller: ESS Technology ES2898 Modem (rev 02)
	Flags: fast devsel, IRQ 3
	I/O ports at b400 [size=8]

It's still disabling the shared IRQ when the modem gets an incoming call signal.  I will try messing with BIOS settings, but this is weird.

---

### Post by Whydoe on 2008-05-25
Only took a little less than a year to fix - but it's fixed.  Moved modem to last PCI slot and all is well.  In moving the modem around to different PCI slots, I was able to completely lock up Ubuntu with an incoming call signal.  So, perhaps, anyone else who has similar problems with IRQ conflicts and such may want to try shuffling around all their cards.  

And no... pci=routeirq or pollirq in grub didn't fix it.

---

### Post by Whydoe on 2008-05-28
What was I thinking.  It's still doing it.  Mouse is ok, but sound is stuttering again.  IRQ conflicts again.  How can I re-enable an IRQ after the kernel disables it without rebooting?  Anyone?

---

### Post by Whydoe on 2008-05-28
I feel like I'm back in 1994 trying to get help getting my Amiga on the bbs/internet.  No big deal.  Fixed the problem.  Should've checked the BIOS and where EXACTLY my PCI cards were.  Sure enough slot 3 and 6 share the same IRQ by default - and, yep, that's where the sound card and the modem were.

---

