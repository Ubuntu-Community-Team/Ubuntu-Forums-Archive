---
title: "Preempt Kernel - irregular occuring graphics problem"
date: 2017-10-06
forum: General Help
---

### Post by cos42 on 2017-10-06
Hello everyone,

I'm using Ubuntu 14.04 (because of ROS Indigo) with a self compiled vanilla preempting RT-Kernel (4.4.75-rt88). I compiled the kernel according to this instruction: [URL="https://ubuntuforums.org/showthread.php?t=2273355"]https://ubuntuforums.org/showthread.php?t=2273355
[/URL]When booting I often run into a black screen ("System is running in low graphics mode") and dmesg reports of nouveau problems reading/writing some memory page. When I then manually run startx the Xserver boots and it's running fine. Moreover randomly the system boots successfully without the black screen.

I suspect this might be a timing issue because of the irregularity of the problem? I considered testing a $sleep 10 or so before the Xserver and nouveau are started - however I'm not so familiar with the startup process of Ubuntu, where should I put this? Or do you have other suggestions?

Thanks in advance!

---

