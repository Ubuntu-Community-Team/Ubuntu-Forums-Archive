---
title: "Grub breaking...."
date: 2007-08-04
forum: General Help
---

### Post by saera05 on 2007-08-04
I'm having a problem where grub keeps giving me errors ("Grub Loading stage1.5read error"). It just started doing this one day, and I hadn't changed any hardware or done anything that I think would cause it. Before this, ubuntu was working just fine. I've tried reinstalling ubuntu, on several different hard drives, but the error isn't going away, although recently I did get a different one - "error 18". 

Does anyone have any ideas what could be causing this? I'm kind of wondering if it's my motherboard going bad, but if anyone has any other suggestions...

---

### Post by TBerben on 2007-08-04
Error 18 is a problem on older computers. Older BIOSes can only read the first 1023 cylinders of a hard drive to check for a bootable OS. So if your kernel isn't located there, its tough luck. The solution is a /boot partition. Reinstall ubuntu, but this time at the partitioner choose manual. As your first partition (hda1/sda1) choose a size of 1023 and a mount point /boot. You can create the rest of the partitions to your liking. Now the kernel wil be located in the first 1023 cylinder section of the hard drive so the BIOS will find it and boot is, after which the kernel can read the rest of the hard drive

[source](http://wiki.linuxquestions.org/wiki/GRUB#Errors_and_solutions)

---

### Post by saera05 on 2007-08-04
I'll try that, but is there a reason it would just suddenly stop working like it did? It previously worked using the guided install...it seems odd that it would be a problem like that with the bios when it had worked previously with the same bios.

---

### Post by TBerben on 2007-08-04
Did you make any changes in BIOS setting? It does sound odd indeed. But GRUB error 18 is explicitly listed as being could by the 1024-problem.

---

### Post by saera05 on 2007-08-04
No, no changes to the bios. Like I said, I reset my computer one day and grub just stopped working. Just recently it's also given me "error 16" ...

---

### Post by TBerben on 2007-08-04
Let's consult our good friend Google about that nasty number 16... See what that means :p

---

### Post by TBerben on 2007-08-04
Hmm.. Error 16 could be caused by a mistake in menu.lst ... Could you post /boot/grub/menu.lst and /etc/fstab please?

---

### Post by merlinus on 2007-08-04
[FONT=Helvetica,Arial,sans-serif]Grub error 16 : Inconsistent filesystem structure
This error is returned by the filesystem code to denote an internal error caused by the sanity checks of the filesystem structure on disk not matching what it expects. This is usually caused by a corrupt filesystem or bugs in the code handling it in GRUB.

You may need to run chkdsk from windows on its partition.

-merlin
[/FONT]

---

### Post by TBerben on 2007-08-04
> **merlinus said:**
> [FONT=Helvetica,Arial,sans-serif]Grub error 16 : Inconsistent filesystem structure
This error is returned by the filesystem code to denote an internal error caused by the sanity checks of the filesystem structure on disk not matching what it expects. This is usually caused by a corrupt filesystem or bugs in the code handling it in GRUB.

You may need to run chkdsk from windows on its partition.

-merlin
[/FONT]

Some people on other forums noted that this could be a simple grub configuration error... I believe I've encountered it myself before, but in my messing around I've seen more errors than I care to remember #-o

---

### Post by saera05 on 2007-08-04
Problem solved: my IDE cable apparently went bad, because replacing it fixed everything.

Thanks everyone for the suggestions, though, I really appreciate everyone trying to help.

---

