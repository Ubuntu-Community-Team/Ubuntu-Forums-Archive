---
title: "Netgear WG311T hangs bootup sequence"
date: 2007-08-13
forum: General Help
---

### Post by scpike on 2007-08-13
I have a fresh install of 64 bit feisty.  It works fine until i plug in my Netgear WG311T pci card.  With the card in the boot sequence halts in "Loading Hardware Drivers" with the message:
error receiving uvent message: No buffer space available 
... ...
ACPI: PCI Interrupt 0000:07:00.0[A] -> GSI 20 (level, low) -> IRQ 20

what does this mean, and does anyone know how to fix it so that I can boot with the wireless enabled? I have already connected via wired and ran apt-get update/upgrade, and I install the linux-restricted-modules to get madwifi for the atheros chipset.
any help would be appreciated, thanks

---

### Post by Darkhack on 2007-08-14
Try some of the following boot commands (Press F6 in GRUB and append them to the line of text at the bottom)

noapic nolapic irqfixup

noapic nolapic irqpoll

noapic nolapic acpi=off irqpoll

noapic nolapic acpi=off irqfixup

Here are four different possible combinations to try.  The last two will disable ACPI however which means that you will not be able to put your computer into sleep mode and if it is a laptop, it will suck the battery pretty quickly since ACPI is necessary for proper power management.  Hopefully one of the first two combinations will work for you though.  Sorry I can't be more specific but this is more of a "guess and check" kind of problem.

---

### Post by scpike on 2007-08-14
Thanks for the advice, but none of those options worked.  Here is lscpi and lshw in case that helps.  It's a Gigabyte P35C-DS3R motherboard, q6600 processor, and the only other card in any pci slots is a nvidia 8600gts.  Any more ideas would be appreciated.

---

### Post by scpike on 2007-08-14
BTW: Tested the card on another computer, it works fine.

---

### Post by scpike on 2007-08-14
Last bump before  I give up on this supposedly well-supported card.  I tried another random PCI card (hauppage tv recorder) and it booted up fine, so its not just a pci bus-kernel problem.  No idea whats going on.

---

### Post by Bealer on 2008-03-22
Just got this exact same problem.

Been switching around the hardware in my pc's.

My WG311T card worked with my AMD Athlon 64 3500+ system, but doesn't with my newer C2D E6300 system.

Did you ever find a solution. I'm trying to run Gutsy. It loads fine with the card removed, but leave it installed and it starts loading, gets to the same message as above, and freezes (doesn't respond to any key presses).

I've tried some boot options, noapic, nolapic, acpi=off etc... I'll try a few more. Really want this to work. It's my brother's pc, and I'm trying to convert him to Linux and this problem isn't helping.

Any ideas?

---

### Post by undertakingyou on 2008-03-23
Interestingly enough, I don't see the card in Spike's lshw or lspci.  I don't know what all that may intail but can you see it in the lspci?  It should show up as a 'Network Controller'.

---

### Post by Bealer on 2008-03-30
Hmmm I think the one I had is a fake. Well it's my brother's.

I have a real WG311T and the card is thinner and has printing on the board itself. His one doesn't it has a sticker, which has an empty box for the serial. It's having problems in Windows too.

I think it's the hardware he's using has highlighted that it's a fake. It doesn't work in his C2D system but does in mine (albeit slow).

---

