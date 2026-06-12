---
title: "ACPI wakeup doesn't work (Edgy)"
date: 2006-12-24
forum: General Help
---

### Post by Balachmar on 2006-12-24
I am trying to get my MythTV box to automatically wakeup and shutdown to record a program.
Unfortunately my motherboard (ASUS A8V-XE) isn't supported by nvram and the guess-helper program returns an empty config file.
So I am turning to the ACPI wakeup method described here:
[http://www.mythtv.org/wiki/index.php/ACPI_Wakeup](http://www.mythtv.org/wiki/index.php/ACPI_Wakeup)
I have installed powersaved so I could get this to work:
$powersave -S
  ACPI
Then I can get and set the time for the RTC.
However it seems to be changed, but as I reboot and check it in the bios, it isn't changed!
How can I fix this. Because leaving the computer on 24/7 is unacceptable.
If I change the setting s directly in the bios it does work.

---

### Post by Balachmar on 2006-12-27
No one, any idea?
Not even on how to get it to work with nvram. Because I can't find anything on my motherboard...

---

### Post by Balachmar on 2006-12-28
OK, a new post, because I think I am somewhat closer to the answer.
At the start of the webpage I mentioned he starts with checking if the kernel supports the acpi functionality needed.
So I checked the kernel the same way he did. Downloading the source and doing the check revealed that it is only supported with the 
/x86_64 architecture.
Downside is, that the generic kernel which is the kernel that would support this, is bugged. It makes my system crash repeatedly for unkown reasons. Others have had this problem as well. So how can I solve this problem now? Should I build my own kernel? And how difficult is that?
OK, hold the presses!
A new kernel isn't needed... What is needed is a little more time... ubuntu-nl chat is working on it with me...

---

