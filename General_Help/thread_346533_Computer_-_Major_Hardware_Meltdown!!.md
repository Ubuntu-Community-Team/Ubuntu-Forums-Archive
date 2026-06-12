---
title: "Computer - Major Hardware Meltdown!!"
date: 2007-01-25
forum: General Help
---

### Post by TheForkOfJustice on 2007-01-25
My old compy (Pentium MMX, made in 1997) broke down. I need help in determining the source of failure. I was running PizzaPup v3.0 Beta 2 with no complaints.
 
Comp started by freezing during normal operation. Happens to everyone.
 
Rebooted. Now it either reboots automatically or freezes. At first it makes it into X but the situation degrades and it doesn't even get passed GRUB.
 
Opportunities to run e2fsck did not correct the issue (though it did correct some regular fragmentation, and inode stuff)
 
I suspected overheating since I had it running overnight and it was old. I check the vents and they are filthy. I clean it inside and out (using canned air) and hope for the best the next morning.
 
No good. Now it no longer shows the BIOS and the monitor just goes to sleep.
The processor's fan has not spun since but power IS getting to the drives. However, I cannot boot from a LiveCD. I removed the HD for safe-keeping. I did give it a polite shake to check the needle (it was fine).
 
My guess is that the motherboard is what got fried and not my HD (or so I pray). Please tell me I am correct and that 2 weeks of work did not get lost.:(

---

### Post by dcstar on 2007-01-26
> **TheForkOfJustice said:**
> 
.......
My guess is that the motherboard is what got fried and not my HD (or so I pray). Please tell me I am correct and that 2 weeks of work did not get lost.:(

Get a new PC, install a Linux system onto it and then plug the old hard drive in and mount it, you will then see if your data still exists.

---

### Post by MrHorus on 2007-01-26
> **TheForkOfJustice said:**
>  I removed the HD for safe-keeping. I did give it a polite shake to check the needle (it was fine).

Sorry you did WHAT?

My understanding has always been that hard drive heads were fragile creatures and should be isolated from such activities as  much as possible so please explain the logic in gaving it a shake to check it as I am curious what this would do and where you learned such a technique?
 
> My guess is that the motherboard is what got fried and not my HD (or so I pray). Please tell me I am correct and that 2 weeks of work did not get lost.:(

It does sound like a motherboard fault to me and you should be able to put the drive in another machine and just mount the filesystem and access your work.

---

### Post by TheForkOfJustice on 2007-01-26
> **MrHorus said:**
> Sorry you did WHAT?

My understanding has always been that hard drive heads were fragile creatures and should be isolated from such activities as  much as possible so please explain the logic in gaving it a shake to check it as I am curious what this would do and where you learned such a technique?

Curiosity got the better of me.  When my uncle's HD failed we could hear a loose needle rattling around in there so I checked for such hoping it wasn't the case.  Should still be fine.  I'm more worried about the constant reboots and shutdowns without proper unmounting and spindown.

> 
It does sound like a motherboard fault to me and you should be able to put the drive in another machine and just mount the filesystem and access your work.

Lets hope so.

---

### Post by tux21 on 2007-01-26
give your 10 yr old pc retirement

---

