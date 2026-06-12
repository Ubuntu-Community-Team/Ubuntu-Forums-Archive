---
title: "Kernel panic : processor context corrupt"
date: 2014-06-17
forum: General Help
---

### Post by Louis_Lourdelet on 2014-06-17
Hi every body,

First of all, I'm french so I maybe won't understand all complicated words related to computers :P
I have a PC HP Media Center 32 bits : 
 - 2 Gio of memory,
 - Intel Core 2 CPU 6400 @ 2.13GHz x 2 processor (I didn't understand  everything, this is just what was displaid by the system details ^^ ), 
 - it says that my graphic card is unknown, I'll try to find which one it is with Windows. Edit : it's a Radeon X1650 SE
- it was running on Vista, I made it run on dual-boot with also Ubuntu  12.04 LTS (everything is ok with the dual-boot)

I  have a kernel panic problem, since the first day I installed Ubuntu, it  happens randomly, once the PC is booted up and during I use it. (it  never happens during the boot). Here's a screenshot of the kernel panic :

[https://dl.dropboxusercontent.com/u/153 &#8230; G_1549.JPG]("https://dl.dropboxusercontent.com/u/15370543/IMG_1549.JPG")
[https://dl.dropboxusercontent.com/u/153 &#8230; G_1550.JPG]("https://dl.dropboxusercontent.com/u/15370543/IMG_1550.JPG")
[https://dl.dropboxusercontent.com/u/153 &#8230; G_1551.JPG]("https://dl.dropboxusercontent.com/u/15370543/IMG_1551.JPG") (this is the right side of the screen, it's only written [OK] ).

I  have tried to find informations about it, but there are so much  different possibilites... And I'm unable to find why it happens, excepted  the fact that it comes from the processor. I thought it came from the  processor temperature, so I changed thermal paste and hoovered the  computer, now Windows runs quite better ^^ but it didn't change a thing with Ubuntu... I've tried to increase the temperature of automatical stop of the processor by the BIOS, but I couldn't access this parameter, and couldn't either change the processor frequency. I also tried to install Ubuntu 14.04 LTS with a USB stick, but I couldn't finish the install before a kernel panic happens... 
So I'd like to know if anyone could tell me first what does the panic screen mean (I'm not able to understand the informations at all...), where  it comes from, and what I can do to stop this :)
Thanks

Edit : it seems to be solved, the explanations are in my post #7 :)

---

### Post by grahammechanical on 2014-06-17
The Detail page showing "graphics unknown" is a bug in the 12.04 Details page that is fixed in 14.04. As for the Fatal Machine Check Exception or MCEs as they are known this is just a little that I have found.

[https://bbs.archlinux.org/viewtopic.php?id=149922](https://bbs.archlinux.org/viewtopic.php?id=149922)

[http://en.wikipedia.org/wiki/Machine-check_exception](http://en.wikipedia.org/wiki/Machine-check_exception)

I also notice that in the first two images there are these messages:

Machine Check Exception 4 bank 5
Machine Check Exception 5 bank 5

Could this be memory? Are the memory modules fitting correctly into their slots? Yes, I do think it has to do with the memory modules.

[http://www.advancedclustering.com/faq/im-getting-mce-machine-check-exception-errors-what-does-this-mean.html](http://www.advancedclustering.com/faq/im-getting-mce-machine-check-exception-errors-what-does-this-mean.html)

[http://h10025.www1.hp.com/ewfrf/wc/document?cc=uk&lc=en&docname=c02662419](http://h10025.www1.hp.com/ewfrf/wc/document?cc=uk&lc=en&docname=c02662419)

You could try running memory check from the Grub boot menu or from the live session. At the first purple screen press Enter then at the next screen select the language and press Enter. At the next screen select Test Memory.

Regards.

---

### Post by Louis_Lourdelet on 2014-06-17
Ok, thanks for this :)
Otherwise, my graphic card is a Radeon X1650 SE
I'll try to see if the memory modules are fitted correcly, and run the memory test. I'll also try to update the kernel.

---

### Post by Louis_Lourdelet on 2014-06-17
So I runned the memory test, but it just said no error had been detected.

---

### Post by Gyokuro on 2014-06-17
MCEs are indicating a CPU problem with mcelog you can decode the MCE message to find out what's wrong and in your case CPU detected a problem with your memory bank 5.

. HTH

---

### Post by garethbaxter on 2014-06-25
Hi I am having a similar problem since I upgraded to 14.04. Is there a main thread for this sort of problem? I see there are quite a few with a handful of replies, but nothing conclusive.

---

### Post by Louis_Lourdelet on 2014-07-31
Hi ! Sorry, I didn't checked this thread since a while... My problem (on 12.04) seem to have been solved since I installed a few things, all is wriiten (in french) here : [http://forum.ubuntu-fr.org/viewtopic.php?id=1606381](http://forum.ubuntu-fr.org/viewtopic.php?id=1606381) . I have followed a part of those advices : [http://forum.ubuntu-fr.org/viewtopic.php?pid=15041961#p15041961](http://forum.ubuntu-fr.org/viewtopic.php?pid=15041961#p15041961), mainly steps C 1-2-3-4.
Hope it will work for you !

---

