---
title: "Windows/Ubuntu/Grub/hardware interaction problem"
date: 2007-09-29
forum: General Help
---

### Post by squigish on 2007-09-29
I'm using a Dell Latitude D610, with a dual boot of Ubuntu Feisty 7.04 and Windows XP Pro.  Last night, it started behaving extremely peculiarly.

My computer will boot successfully into Ubuntu or into windows safe mode, but not into windows normally.  I get past the boot loader (GRUB), and the windows boot screen, but then the screen goes black and the computer is totally non-responsive.  The "use last good settings" option has the same results as a normal boot.

This seemed like a software issue, but justs to make sure, I swapped out the hard drive for another, brand-new refurbished dell hard drive, which had an image of my hard drive from a month ago installed onto it, which also was a dual-boot windows/ubuntu with a GRUB boot loader.  I put that hard drive into my computer, and my hard drive into another latitude d610.  The symptoms followed the computer, not the hard drive, as my installation of windows, which couldn't boot successfully on my computer, booted without issue on the other latitude machine.  Likewise, the old installation, which worked fine on the other computer, exhibited the same symptoms on my computer.  

Just for kicks, I tried booting using a third hard drive, this one with only a single operating system (windows xp pro), and it worked fine on both computers.  

I'm really baffled.  I just reinstalled ubuntu earlier tonight on the spare hard drive using the spare latitude, and I haven't made any significant system changes to the primary hard drive recently, and indeed, haven't removed it from the machine until it started acting up.

Is a GRUB install specific to a certain machine?  Does it install anything elsewhere than the hard drive? That's the only explanation I can think of for why the problem stays with the machine, not the hard drive.  The two Dells are configured similarly, but not identically.

---

