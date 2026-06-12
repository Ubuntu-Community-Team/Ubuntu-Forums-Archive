---
title: "Vanilla kernel not booting with Edgy"
date: 2006-11-30
forum: General Help
---

### Post by quini on 2006-11-30
Hallo!

I've compiled vanilla 2.6.19 kernel with ck1 & linux-phc patches using make-kpkg with no problem, but when trying to boot from it it stops, then (after a couple of minutes) it says it cannot get to the root partition, showing edgy fstab's UUID data.

Is there any trick I should know?  Is an ubuntu 2.6.19 linux-source going to be available soon?  

TIA  ;)

---

### Post by ispmarin on 2006-11-30
Please, post exactly what the message is. I will guess, thought: the problem is that you neither made a initrd image or compiled the ide/sata modules and the chipset module in the kernel. What mainboard/chipset? IDE/SATA? Ext3, reiser?

---

### Post by kilou on 2006-12-08
Can't help for your particular problem but I can say that vanilla kernel 2.6.19 patched with linux-phc works with Edgy for me. Check this thread:
[http://www.ubuntuforums.org/showthread.php?t=314264](http://www.ubuntuforums.org/showthread.php?t=314264)
and this guide:
[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

---

### Post by quini on 2006-12-23
Thank you for your answers.

I've now compiled vanilla 2.6.19 with ck2 and phc patches, using .config from feisty's linux-image-2.6.20-2-generic, with no changes at all, and this time it boots fine, so I must have changed something important when compiling the first time.

Thanks for your time  :p 

PD I'm sorry for the delay (too much work!) ;)

---

