---
title: "Laptop not shutting down correctly...."
date: 2020-05-22
forum: General Help
---

### Post by Furycd001 on 2020-05-22
HI.. I have a Lenovo Ideapad 330 running Xubuntu 18.04 that is failing to shutdown or reboot correctly. I select shutdown or reboot and the laptop starts shutting down as normal. The splash screen disappears & the screen turns off, but the power button & other keys like numlock stay turned on. I've tried leaving it alone for up to 10 minutes, but nothing happens until I hold down the power button for five seconds. I have also been experiencing some freezes were the entire system has locked & have had to hold the power button to reset. Everything was running fine until two days ago when this problem just appeared out of nowhere. Any help would be much apprechated thanks.



> **LAPTOP SPECS**
Kernal x86_65 Linux 5.3.0.53-generic
CPU = AMD Ryzen 5 2500U with Raedon Vega Mobile Gfx @ 8x 2GHz
GPU = AMD RAVEN (DRM 3.33.0, 5.3.0-53-generic, LLVM 9.0.9

---

### Post by Rex Bouwense on 2020-05-22
I have a similar problem and am also running Xubuntu 18.04  (My CPU is an AMD Ryzen 3 3200U with Radeon Vega Mobile Gfx)  It started to occur after I upgraded the kernel to 5.3.0-53.  I tried a few things as you probably did, like reboot and log out, without success.  I have reverted to loading the previous kernel, 5.3.0-51, that I had installed.  I can only assume that something in the kernel upgrade caused the malfunction because the computer now is shutting down normally.  I realize that this is not a fix but it is a work around and will prevent you from having to do a hard shutdown every time that you want to shut down the computer.

---

### Post by mörgæs on 2020-05-22
Maybe time to try a newer kernel. Does a live boot of 20.04 shut down properly?

---

### Post by ajgreeny on 2020-05-22
Just in case this helps, though in my case it's 20.04 that occasionally hangs, try pressing Esc when the system is shutting down which should bring you to the text scroll.

In my 20.04 when the problem happens I see the line 
***A stop job is running : snapd.service (1m:30s)***
The time shown in brackets counts down to zero and then finally the machine shuts down properly.

I have found how to reduce this wait-time by editing the configuration file with ```
sudo nano /etc/systemd/system.conf
``` changing the line 
***DefaultTimeoutStopSec=90s*** 
to 
***DefaultTimeoutStopSec=10s***

This does not really answer the question of why the delay happens in the first place but it does reduce that time delay by 80 seconds, and I have not seen any problems as a result of unclean shutdowns since making the edit.

Your reason for delay may, of course, be totally different from mine so proceed with caution.

---

### Post by Furycd001 on 2020-05-22
Thank you everyone for replying. Can confirm that the problems have only started appearing recently and now that I think about it, there was a kernel update included with a recent update (I usually update once a week via command line). Will try reverting back to the previous kernel and see if that fixes the issue. I've tried pressing "ESC", tried waiting for a number of minutes & the screen definitely looks like it's off rather than in suspend....

---

### Post by Furycd001 on 2020-05-23
So the problem was kernel related & I managed to fix or find a "work around".


1. In a terminal I typed **uname -r** to check which kernel was currently being used.....

2. After that I done **ls /boot/** to check which kernels were installed.....

3. Next I done **sudo nano /etc/default/grub** & changed **GRUB_DEFAULT=0** to be **GRUB_DEFAULT="1>2"**....

4. And finally I done **sudo update-grub** & then rebooted the system when done....

5. Once rebooted I open up a terminal & typed **uname -r** to check that I was successfully using the previous kernel....

---

### Post by THUNDER233 on 2020-05-24
Similar problem on my main computer.
Occurred after updates on 20 May 2020.

Screen shuts down "No Signal"
Computer continues to run.
Disc drive does not shut down.
Only way to restart computer is with hard reset
Used instruction above.
Computer now shuts down properly.
 ls /boot/ shows two kernels:
5.3.3-51-generic and 5.3.0.53-generic
Now using -51-generic

Thanks   P.S.  should we send bug report -next kernel will likely break comp. again

---

