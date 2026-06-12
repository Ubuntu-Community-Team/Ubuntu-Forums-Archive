---
title: "Brightness control Toshiba laptop with Gallium 0.4 on ATI RV515"
date: 2014-09-08
forum: General Help
---

### Post by lennart3 on 2014-09-08
Hi,
I have been using 14.04 for quite a while now and - generally - I am very  pleased with the performance.
BUT - there is still a problem regarding brightness control in my Laptop Toshiba satellit A100-163.
From the start there have been a problem regarding non-controllable brightness.
From beginning the brightness settings were not doing anything - I tried fixes suggested and the solution
I use now is the brightness control program, but it is resetting the brightness settings at each new boot.
But - a new thing happened after the last  system updates- now the brightness is set to max in the settings
but sliding down the brightness contol slider does nothing....
So - again- is there really no solution to this problem ??
The graphic card in this laptop is Gallium 0.4 on ATI RV515.
Thankful for help !

---

### Post by varunendra on 2014-09-11
Hello lennart3,

I'm not a video issues troubleshooter, but it may help to post if you had manually added/changed something in some system files, and what.

For now, I think you should at least post back the outputs of -
```
cat /proc/cmdline
cat /etc/rc.local
for i in /sys/class/backlight/*; do echo -e "\n $i"; cat $i/{brightness,max_brightness,actual_brightness}; done
```

And can you post the link to the guide/post that you previously followed to solve your problem?

---

### Post by sofiapara on 2015-05-02
Hi, 

I also do not have control over my brightness...my processor is AMD A6-6310 APU with AMD Radeon R4 Graphics × 4 and my graphics Gallium 0.4 on llvmpipe (LLVM 3.4, 128 bits).
So far I have read quite a number of suggestions but not for such a graphic environment..

When I type: cat /proc/cmdline

the output is:

BOOT_IMAGE=/boot/vmlinuz-3.13.0-51-generic root=UUID=2ae0feaf-6035-4468-984d-6ae0e6e9148e ro acpi_osi=Linux quiet splash acpi_backlight=vendor vt.handoff=7

When I type: cat /etc/rc.local

the output is:

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0

And for: for i in /sys/class/backlight/*; do echo -e "\n $i"; cat $i/{brightness,max_brightness,actual_brightness}; done

the output is:

 /sys/class/backlight/ideapad
8
11
8

Any help to relax our eyes is more than appreciated!! :D 

Sofia

---

