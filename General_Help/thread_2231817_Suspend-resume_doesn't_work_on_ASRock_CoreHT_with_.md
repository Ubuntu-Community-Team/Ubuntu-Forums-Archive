---
title: "Suspend-resume doesn't work on ASRock CoreHT with ubuntu 14.04 64-bit"
date: 2014-06-28
forum: General Help
---

### Post by ivo2 on 2014-06-28
Hi,


I have tried a lot of things I've found on the internet, but I am not able to get suspend and resume working. However hibernate works fine. Maybe anyone here can help me.


I used to ran ubuntu 12.10 32-bit and suspend worked fine. I upgraded to 14.04 64-bit and I am very satisfied with the improvements on performance. The only thing is that suspend doesn't work anymore and I really like to use this feature.


Suspend seems to work fine, but when I resume the system freezes. After the system powers up, I get a frozen screen (screenshot as before the system turned off) and the CPU seems to stall. Keyboard and mouse ain't working either. I need to push the power button for some seconds to turn off the system. The strange thing is that once in about 20 times resume (partly) works. If I have a look at 'pm-suspend.log', the last line is 'performing suspend'. It never wakes up ...


I assume the issue is video-card related. I have an intel GPU (sandy-bridge), using i915 driver. When I switch off kms mode (nomodeset or i915.modeset=0 boot option), suspend seems to work correctly. Only video is crappy (before suspend) and I don't get video after resuming. But I can login from and ssh shell and operate the system.


I tried a lot of options, but none seem to solve my issue:
* tried various i915 boot options
* tried pm-suspend quirks
* tried various modes on /sys/power/pm_test
* installed s2ram and tried all options
* tried a lot of options in /etc/pm/sleep.d (but this state isn't reached after resume, because the system stalls before)
* tried suspend this only text screen and no X
* tried a lot of kernels (ubuntu kernels and mainline from version 3.9 to 3.15, even intel drm versions) but none worked.


I hope someone can help me with this issue. If you require more information or logfiles, please ask me.


Thanks in advance.
Ivo.

---

### Post by ivo2 on 2014-08-21
To whom is interested, I found the solution to let suspend work.

I really tried a lot of things, like a lot of kernel acpi command line parameters and finally the following parameter solved the issue:

acpi_sci=low
I don't know why (probably the interrupt is active low) but after adding this parameter suspend/ resume never went wrong.

Best Regards,
Ivo.

---

### Post by sandyd on 2014-08-21
Hi, please mark this thread as solved via Thread Tools -> Mark Thread as Solved if you have found a solution.

Thanks!

---

