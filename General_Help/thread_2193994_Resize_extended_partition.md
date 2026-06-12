---
title: "Resize extended partition"
date: 2013-12-15
forum: General Help
---

### Post by ka2012 on 2013-12-15
I am dual booting windows 7 and ubuntu 12.04 Here's a screenshot of my gparted:
[ATTACH=CONFIG]248629[/ATTACH]
The first two are windows, then I have a data patition, then 32 GiB of unallocated space, and then an extended partition with Ubuntu, swap, and windows recovery. I want to make the extended partition bigger (using the unallocated space) so I can make another logical partiton. I booted with a live cd and tried to resize it to use the unallocated space, but I got this message, so I didn't apply the changes...
[ATTACH=CONFIG]248630[/ATTACH]
I would just like advice on how to safely resize the partition without messing up my existing stuff...thanks in advance for any help

---

### Post by grier-devon on 2013-12-16
This is a common error message, I know when I have removed Ubuntu from some machines doing a dual boot and I extend the partition for Windows I have to fix the MBR using console. I am unsure how to do this in Ubuntu but once you extend the drive you will have to fix the boot. I will see if I can find a guide or maybe someone else may shed some light on the subject.

---

### Post by sammiev on 2013-12-16
I would boot from a live gparted USB/DVD/CD and then extend the partition. Remember the first thing to do is make a backup before doing anything.

---

### Post by ka2012 on 2013-12-16
> I would boot from a live gparted USB/DVD/CD and then extend the partition.
Thats what I did do, but I got that error message so I stopped. I just want to know if anything bad would happen if I continued/how to resize it safely. After I clicked "ok" the table looked fine on gparted, but I don't know if anything bad would have happened if I actually applied it.

Also I would like to clarify that I don't want to make the ubuntu partition bigger, just the extended partition that it is in[[COLOR=#000000][/COLOR]]("http://ubuntuforums.org/member.php?u=1848398")

---

### Post by sammiev on 2013-12-16
Your /dev/sda4 as well as /dev/sda7 would increase in total size. Increasing or decreasing on the back side of a extended partition usually creates little to no problems but can on the front side. Always backup everything first before you make any changes of any kind.

---

