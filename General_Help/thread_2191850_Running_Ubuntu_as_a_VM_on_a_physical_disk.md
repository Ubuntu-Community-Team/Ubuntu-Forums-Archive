---
title: "Running Ubuntu as a VM on a physical disk"
date: 2013-12-04
forum: General Help
---

### Post by michael.kyritsis on 2013-12-04
I have Ubuntu installed and working on an external disk (which plugs in via USB), and I have Windows 7 installed on the internal hard drive, so it's effectively a dual-boot (if I plug in the external disk before starting the machine it boots up in Ubuntu, if not it boots up in Windows). But I also want to run the same Ubuntu machine in a VM.  In the Windows installation I have VMWare player, and I've created a new VM (type Linux, version Ubuntu-64 bit), and attached PhysicalDisk1 (which is the external disk).   At this point I ran into the infamous "a virtual cpu has entered the shutdown state" problem.  The problem was that in VMWare I'd included just one partition of PhysicalDisk1 - actually there is only one partition on that disk.  I was looking at the partitions because I wanted to be 100% sure that it's PhysicalDisk1 I should be using, and not PhysicalDisk0, which would have corrupted my Windows 7 installation and left me in a real mess because it's an encrypted volume so I would have lost everything.  When I included the disk PhysicalDisk1 in VMWare instead of just the one partition I was able to boot up the VM. I can now get as far as grub, and after that the log in screen. Currently once I've logged in I get a black screen, and am still trying to figure out what the problem is there, but I thought I'd share my progress so far.  

I must give credit to "harky" who shared a similar problem, and that's what made me think along the lines of partitions, otherwise I'd never have thought of it.  His issue is different (and the solution unavoidably more messy as a consequence) but my situation is a bit simpler because I have an entire disk (the external one) dedicated to Ubuntu.  [http://ubuntuforums.org/showthread.php?t=1793371](http://ubuntuforums.org/showthread.php?t=1793371)

---

