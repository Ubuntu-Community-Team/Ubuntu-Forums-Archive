---
title: "Being Green : Power Management Question."
date: 2008-07-02
forum: General Help
---

### Post by melgish on 2008-07-02
**What do I have to work with?**

Ubuntu 8.04 Server edition running VMWare Server 2.0 RC 1

**What do I want to accomplish?**

I want my server to shut itself down every day at about 5:00 PM local time, and then start itself up the next normal workday (I'll forgive holidays) at about 5:30 AM local time.

In the ideal world, it should gracefully shutdown any VM's that are running, and start them back up again, accounting for any that are automagicly started by VMWare server.

**Why do I wish this?**

In 3 words: My Power Bill.  I use this device to host dev/test environments for my job. I work from home, and they don't reimburse me for electricity.  

**What I can do on my own?**

I'm an accomplished Windows developer (don't hit me) with a fair (but rusty) amount of experience in C++.  Ubuntu / Linux is still 'the other OS' but I'm learning more each day.

** Where I'm at in this project?**

Using [_this link_]("https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake") I've managed to figure out the mechanics of off and on.  I also know how to generate a list of VM's that are currently running.

**What I'm missing?**
[LIST=1]
[*]The best way to determine what 'the next work day' is.  I know (a bit) about the date command, are there any date-calculation commands or do I need to do the math on my own?
[*]How best to determine if a VM is set to auto-start
[*]The best way to save my list of VM's that I'll need to start on boot
[*]The best place to hook into the start process to launch any vms that were running (and not already started)
[/LIST]

Any help I can get from the community would be greatly appreciated!

---

### Post by melgish on 2008-07-06
> **melgish said:**
> **What I'm missing?**
[LIST=1]
[*]The best way to determine what 'the next work day' is.  I know (a bit) about the date command, are there any date-calculation commands or do I need to do the math on my own?
[*]How best to determine if a VM is set to auto-start
[*]The best way to save my list of VM's that I'll need to start on boot
[*]The best place to hook into the start process to launch any vms that were running (and not already started)
[/LIST]

Any help I can get from the community would be greatly appreciated!

Thanks to everyone who's helped me so far. :)  I worked out that the 'date' command has all the answers to calculating 'monday or tomorrow' only to find out that my box ignores the date part of /proc/acpi/alarm. The machine is starting up every morning.

I guess this simplifies my logic a bit.  No need to be so complex. Now it's "always shut down at 5:00 PM" and "always start at 5:30 AM" ... later I can work on "if it's the weekend, go back to sleep."

---

