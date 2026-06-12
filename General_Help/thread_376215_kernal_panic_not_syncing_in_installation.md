---
title: "kernal panic not syncing in installation"
date: 2007-03-04
forum: General Help
---

### Post by phelix17 on 2007-03-04
Day 2 of not being able to install any version of Ubuntu.

I read a lot of other threads so here is what I've done. I've checked out the hardware, did memory test and my memory passed. I have made a number of Ubuntu iso disks per the Ubuntu directions, buth 6.06, 6.10 and 6.10 alternate. Every time I try to install I get the Kernal panic - not syncing  Attempted to kill init.

My computer is p4 2.4
512 ram
250 G Seagate HD with a 10 G partition in fat32 in anticipation of installing Ubuntu

I have copied the disks in infra recorder per instructions at a snails pace.

Anyone have any ideas why this won't work? This computer worked with windows three days ago. I cleaned the hard drive completely of windows materials and then put it into another computer to initialize and make the partition and run diagnostics just to make sure HD was working well. I can't believe I can't make this work.

Any help is appreciated.

---

### Post by TheFinale on 2007-04-20
I'm getting the Same problem on my Parkard Bell Easy Note R1 While attempting to install Ubuntu Ultimate 1.3
Any ideas how to fix this? 
I burned the iso to a DVD-RW using Nero.

Thanks in advance.

---

### Post by emperon on 2007-04-20
try noapic nolapic nosmp boot options

---

### Post by TheFinale on 2007-04-22
I just solved my own problem.

ACPI=Force

Thanks for the Help.

---

