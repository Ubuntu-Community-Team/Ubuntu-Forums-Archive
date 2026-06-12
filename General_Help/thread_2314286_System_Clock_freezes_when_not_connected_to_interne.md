---
title: "System Clock freezes when not connected to internet"
date: 2016-02-19
forum: General Help
---

### Post by User1436 on 2016-02-19
Hi everybody,

I'm having a weird issue with the clock on my system. When I&#8217;m not connected to the internet the system locks up and the clock freezes. Most of the time when I move the mouse the system catches back up to real time. I have already replaced the CMOS battery in my laptop, but that hasn't fixed the issue. I have tested the hardware clock by turning the laptop off, pulling the battery and the power cord for 24 hours and then booting up and entering the BIOS setup screen and checking the time on the HW clock. The time on the HW clock is accurate. But when I'm using my laptop offline it freezes up randomly. The clock in the system tray stops and programs lock up. I can't even Ctrl+Alt+F1 to get to the console. I have tried changing the Video driver and that hasn't helped either. 

Here's my setup:
Lenovo W700
Kubuntu 15.10 with latest updates
Linux Laptop700 4.2.0-27-generic #32-Ubuntu SMP Fri Jan 22 04:49:08 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
NVIDIA Corporation G92GLM [Quadro FX 3700M] (rev a2)

Any help or suggestions on where to look next would be great!

Thanks!!

---

### Post by Linuxisfast on 2016-02-20
Right click on clock, time and date setting set the time setting to manual from automatic.

---

### Post by User1436 on 2016-02-20
@Linuxisfast I tried your suggestion and the clock lost 50min in 3hours.   Thanks for trying!

---

### Post by ik-0 on 2016-02-20
does this help:  [http://www.linuxquestions.org/questions/linux-newbie-8/disable-hardware-clock-syncronisation-by-kernel-943877/](http://www.linuxquestions.org/questions/linux-newbie-8/disable-hardware-clock-syncronisation-by-kernel-943877/)

---

### Post by User1436 on 2016-02-20
> **ik-0 said:**
> does this help:  [http://www.linuxquestions.org/questions/linux-newbie-8/disable-hardware-clock-syncronisation-by-kernel-943877/](http://www.linuxquestions.org/questions/linux-newbie-8/disable-hardware-clock-syncronisation-by-kernel-943877/)  Thanks for the suggestion, but the system is still losing time.

---

### Post by sammiev on 2016-02-20
I ran into the same problem on another type of laptop for years. Tried the cmos battery a few times and all but still had the same problem.

Updated the BIOS and never had problems again.

Just saying.

---

### Post by User1436 on 2016-02-20
Thanks for the suggestion, I completely forgot to check that. But still no go. Laptop is still losing time and freezing.

---

### Post by ik-0 on 2016-02-23
download and burn/flash Ubuntu 14.04 and live boot it.  see if running off the live disc changes anything.  This will help you identify if the problem is configuration, kernel version related, or a hardware problem.

---

### Post by User1436 on 2016-02-28
@ik-0

I did as you suggested and when running off the live CD the clock kept perfect time for 4 days when disconnected from the internet. I'm guessing it's a kernel thing. I'm going to try compiling my own kernel config to see if that fixes the issue.

Any suggestions on how to do that are welcome.

---

### Post by User1436 on 2016-03-05
Ok, compiling my own kernel proved to be a pain in the butt. Building a kernel on Gentoo is soooo much easier. So I loosely followed the directions at:

[http://linuxg.net/how-to-install-kernel-3-19-5-on-ubuntu-15-04-ubuntu-14-10-ubuntu-14-04-and-derivatives/](http://linuxg.net/how-to-install-kernel-3-19-5-on-ubuntu-15-04-ubuntu-14-10-ubuntu-14-04-and-derivatives/)

And got the kernel from:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

And installed kernel 4.1.11, now everything is running smoothly!

Thanks for everyone's help!!!

---

