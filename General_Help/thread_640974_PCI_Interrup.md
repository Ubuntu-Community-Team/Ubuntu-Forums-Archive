---
title: "PCI Interrup"
date: 2007-12-14
forum: General Help
---

### Post by foamy3 on 2007-12-14
I just brought my PC back home for winter break and now it won't boot into linux.  I'm using Ubuntu Feisty (I could never get gutsy installed right). It hangs at the "starting..." screen when I try to boot.  In recovery mode, it hangs with the text
"[1.118078] ACPI: PCI Interrup 0000:01:00.0[A] -> GSI 21 (level, low) -> IRQ 19"

I have dial-up internet here at home, so I won't be able to download a new disk to reinstall until January.  I have a couple other live cds and a working windows installation, though.  Do you know any way I can take care of this problem without reinstalling?  I don't know why it messed up.  It was working fine when I used it last at school.

---

### Post by geraldm on 2007-12-16
There are reported problems on acpi, and some suggestions are responding with 
adding options on the kernel line at boot. 
One suggestion was add "acpi=no" to the end of the kernel line.
Another suggestion was add "noapci noacpi" at the end of the line.

Always backup the file before making any changes.  The file is /boot/grub/menu.lst
Add the parameter(s) to the line beginning with "kernel" if you want to try this.
You might google for the answer.  I tried google with "acpi=no" and got some results. 

Gerald

---

### Post by foamy3 on 2007-12-16
I tried both of those and it still hangs with the same error.  I did those with the edit command in grub.  It won't make any difference if I do it in menu.lst, will it?

---

### Post by geraldm on 2007-12-16
No difference.  Typing on the command line is enough to test.
I thought from the line you posted that there were two possible problems, the interrupt, and acpi.  Using the kernel line to test acpi start should have covered both possibilities, I thought.
These were to test the kernel recovery mode version.

There may be a different problem in the regular version, which is stopping at "starting..."
If no one has any other suggestions, then you might try looking into bug reports to get some other ideas.

Gerald

---

### Post by foamy3 on 2007-12-20
I just found an old Dapper live cd I was going to boot live to recover some data, but I couldn't get it to boot, either.  When I started it, it stopped at the first line saying something along the lines of "Loading kernal....Ok"

The fact that it's messing with a live cd leads me to believe it's nothing on the harddisk that's wrong.  Do you think it's a BIOS problem?  I'm trying to get that updated now.

---

### Post by foamy3 on 2007-12-21
Flashing the BIOS didn't help...

The live cd didn't boot so I would say it isn't a harddrive error.  And since I flashed the BIOS to no sucess, I would say it wasn't the motherboard, either.  Vista boots on it fine, so it really can't be a hardware problem.  What else would stop a boot?

---

### Post by foamy3 on 2007-12-22
Hmm.. I just found an old edgy cd and that boots fine.  There must just be a problem with the dapper one.  But that still doesn't solve my not booting ubuntu from my harddrive problem...

---

