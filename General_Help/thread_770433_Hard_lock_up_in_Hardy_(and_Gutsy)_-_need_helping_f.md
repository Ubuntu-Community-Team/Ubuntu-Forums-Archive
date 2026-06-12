---
title: "Hard lock up in Hardy (and Gutsy) - need helping figuring out why"
date: 2008-04-27
forum: General Help
---

### Post by mykrob on 2008-04-27
Hey-

Did a clean install on a friend's computer of Kubuntu Hardy. It freezes hard at random to where the keyboard and mouse do not respond. I have to perform a hard reboot. It did this in Gutsy for him as well. I have put in the boot parameters of noapic, nolapic, and acpi=off. I almost got 24 hours out of it after adding the acpi=off. But it was frozen solid this morning again.

I have looked through the log files, but I probably dont know what I'm looking for. I ran a full cycle of Memtest, and it came up fine. Tested the harddrie using Seagate Powertools, it is fine. I cleaned out the case with compressed air to make sure the cooling fins were not clogged.
Can someone help me figure out why this is freezing?

Thanks,
-myk

---

### Post by ghost_ryder35 on 2008-04-27
What is the hardware he is running?  do you know how hot the cpu is getting?  might also want to look into the power managment options under system, administration, power managment.  Does it happen in the middle of working on something like surfing the web, or only when the computer is idle?

---

### Post by mykrob on 2008-04-27
i have only witnessed it when it is sitting idle. The user reports the same thing historically. I just got through combing through the BIOS and disabled some options regarding suspend, i hope that will fix it. I also turned off ACPI in the BIOS.

I also removed the nVidia video card and am trying the onboard, because now, after the initial boot screen, i get no picutre for the login screen, just a black monitor. Working with the onboard video, will test for several hours. Maybe the video card was going bad..

-myk

---

### Post by mykrob on 2008-04-27
here are the results from grep "error" /var/log/*

[http://pastebin.ca/999808](http://pastebin.ca/999808)

got a lot of these:

> 
#
sector 4192
#
/var/log/kern.log:Apr 25 17:53:43 fudoshinka kernel: [ 2584.317733] Buffer I/O error on device sr1, logical block 1048
#
/var/log/kern.log:Apr 25 17:53:43 fudoshinka kernel: [ 2584.317743] Buffer I/O error on device sr1, logical block 1049
#
/var/log/kern.log:Apr 25 17:53:43 fudoshinka kernel: [ 2584.317750] Buffer I/O error on device sr1, logical block 1050
#
/var/log/kern.log:Apr 25 17:53:43 fudoshinka kernel: [ 2584.317755] Buffer I/O error on device sr1, logical block 1051
#
/var/log/kern.log:Apr 25 17:53:43 fudoshinka kernel: [ 2584.317760] Buffer I/O error on device sr1, logical block 1052
#
/var/log/kern.log:Apr 25 17:53:43 fudoshinka kernel: [ 2584.317765] Buffer I/O error on device sr1, logical block 1053
#
/var/log/kern.log:Apr 25 17:53:43 fudoshinka kernel: [ 2584.317769] Buffer I/O error on device sr1, logical block 1054



Dont know what this means, but right now, its been 6 hours since I pulled the video card and switched to the onboard. So far, so good, but if anyone can provide more info on these errors from the log, that'd be great.

Thanks,
-myk

---

