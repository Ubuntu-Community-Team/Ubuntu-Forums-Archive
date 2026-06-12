---
title: "[SOLVED] Clock Problems.."
date: 2007-09-30
forum: General Help
---

### Post by darren_07 on 2007-09-30
Hi everyone..

I have Ubuntu installed on an external USB hard disk (which works a treat) however the problem im having is the clock never has the correct  time.  
If i change the time in Ubuntu and return to Windows the time is out in windows by about 9 hours or so.. If the time is set correctly in windows and i boot of the external Hard drive to Ubuntu then the time is about 2 hours slow.. 

Has anyone come across this problem is so do you know how to fix it??

Cheers
D
:confused::confused::confused::confused:

---

### Post by redtrak on 2007-09-30
I had a similar problem before.
In terminal type:
```
sudo gedit /etc/default/rcS
```
Change "UTC=yes" to "UTC=no".

---

### Post by darren_07 on 2007-10-02
Thanks for your reply however...
i tried this and i still have the same problems...

any more idea???

:confused::confused::confused:

cheers
D

---

### Post by GSF1200S on 2007-10-02
There was something about this problem in an Arch Linux install guide (not the official one). I dont remember it exactly, but ill take a look when im off of work..

---

### Post by stunti on 2007-10-02
Hope some will give an answer because I have exactly the same problem with the same configuration (don't know if it's related or not).
Feisty on USB HD and windows on regular HD.
I have 8 hours diff between the 2 OS.

---

### Post by GSF1200S on 2007-10-02
> **stunti said:**
> Hope some will give an answer because I have exactly the same problem with the same configuration (don't know if it's related or not).
Feisty on USB HD and windows on regular HD.
I have 8 hours diff between the 2 OS.


I wonder why I havent had this problem? I dual boot XP and Buntu, so I would think the problem would be there. Once again, I know this was mentioned in an Arch Linux install guide somewhere.. so you can look around. Hell, im curious as to what causes that now. I would think that UTC would eliminate that problem as it d/ls the exact time from a server.

---

### Post by w4ett on 2007-10-02
One other thing to check is the system bios clock.  Boot into your bios and reset the clock.  Might be you have a failing CMOS battery.  Also in windows and Ubuntu, make sure your timezones are setup correctly, and that you have enabled NTP support in Ubuntu and time sync in Windows.

---

### Post by stunti on 2007-10-02
> **w4ett said:**
> One other thing to check is the system bios clock.  Boot into your bios and reset the clock.  Might be you have a failing CMOS battery.  Also in windows and Ubuntu, make sure your timezones are setup correctly, and that you have enabled NTP support in Ubuntu and time sync in Windows.

The clock is nowhere to be found in my BIOS (HP pavilion zt3360AP).
Laptop bios are really useless.

Timezone are the same on both OS as welll as NTP server.

Thanks
Cheers

---

### Post by stunti on 2007-10-02
from [http://wiki.archlinux.org/index.php/Official_Arch_Linux_Install_Guide](http://wiki.archlinux.org/index.php/Official_Arch_Linux_Install_Guide)

> 
/etc/rc.conf
HARDWARECLOCK 
Either UTC if your BIOS clock is set to UTC or GMT, or localtime if your BIOS clock is set to your local time. If you have an OS installed which cannot handle UTC BIOS times correctly, like Windows, choose localtime here, otherwise prefer UTC, which makes daylight savings time a non-issue and has a few other positive aspects.


will try that tonight.

---

### Post by darren_07 on 2007-10-04
Hi Guys thanks for the response..

I think found a solution..  (seems to work for me) i believe its the UTC however the Linux clock also has under the properties a tick box which was still turned on for the UTC (as i was modifying the RCS file (mentioned earlier in this forum) .. i ticked it off and the planets seem to align... 

Hopefully this solved the problems for others as it really really annoying when the clocks wrong...
(funny how its the smallest things bring us down) :)

Cheers
D
Happy days.... as i can now tell the correct time....
:guitar:

---

