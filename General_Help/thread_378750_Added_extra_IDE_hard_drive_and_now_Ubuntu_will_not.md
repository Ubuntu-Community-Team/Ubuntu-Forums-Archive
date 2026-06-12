---
title: "Added extra IDE hard drive and now Ubuntu will not boot"
date: 2007-03-07
forum: General Help
---

### Post by riverotter on 2007-03-07
Hello,

I have a triple boot with Vista, Ubuntu and Fedora Core 6.
System details: Core 2 Duo 1.83, Motherboard: P5W DH Deluxe, 2x250 SATA HD RAID 0 (RAID was set up with jumper settings on MB), 1 x IDE HD (just added). Fedora GRUB. 

All three OS were working fine. I added an extra PATA IDE drive (seperate connection to DVD), and booted up. GRUB works fine. Vista works fine. Both Ubuntu and FC6 now hang on boot at the very early stages. Formated the PATA as FAT32 and it's a "logical drive".

I then unplugged the power (only) for the PATA and rebooted, and although Ubuntu got further in booting up, still ended up hanging (with SATA drive LED on) (I think, unless I'm impatient!). 

Any suggestions? Maybe something needs tweaking in the BIOS? 

Many thanks!

---

### Post by ajgreeny on 2007-03-07
Has the extra drive taken the name of one that was there before?  ie, has it now become, for example, sda1 and moved the nomenclature of all the others up or down the numbers scale?

Try booting into ubuntu live CD and see what "fdisk -l" in a terminal tells you, then mount the ubuntu partition and try viewing your /boot/grub/menu.lst file to see if everything points to the right partition for what you're trying to boot.

---

### Post by riverotter on 2007-03-07
Hi thanks. I booted with the live cd, but it didn-t work. So tried with the alternative ubuntu cd and started getting these messages:

*Disabling IRQ #58* (and later *#74*)

*hde: lost interrupt* (several of these)

everything was very slow. Finally, once into the installation screen, nothing happened - it just stopped. 

So I tried with the FC6 DVD, and typed "resuce linux" and exactly the same thing happened as with Ubuntu. 

Is there some confusion between the SATA, IDE and the CD Rom? Should I try this with the PATA unplugged (but what would I gain?). 

Thanks again

---

### Post by riverotter on 2007-03-07
Not sure if this recent post is of any help, but exact same motherboard:

[http://ubuntuforums.org/showthread.php?t=363596]("http://ubuntuforums.org/showthread.php?t=363596")

CD/DVD in my case is not SATA connection, but normal IDE.

---

### Post by riverotter on 2007-03-07
ok - solved (partially) - I'll post this for others who are having this problem. 

first another relevant post:

[http://forums.fedoraforum.org/archive/index.php/t-135886.html]("http://forums.fedoraforum.org/archive/index.php/t-135886.html")

It would appear to be a problem with jmicron which loads the drive after the bios on the p5W DH deluxe. By disabling jmicron in the bios, will allow all OS to boot as normal. Unfortunately by stopping Jmicron, there is no PATA drive! But at least I-ve got Linux back. 

Therefore jmicron and linux do not work together (does work with Vista though). Next will try with another internal sata drive and try that instead...

---

