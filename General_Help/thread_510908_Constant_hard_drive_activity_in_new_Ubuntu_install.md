---
title: "Constant hard drive activity in new Ubuntu install"
date: 2007-07-27
forum: General Help
---

### Post by Stratis on 2007-07-27
Hello!

I have a problem with my new Ubuntu install (installed yesterday) on a Sony Vaio desktop; 
the hard drive is constantly active.

The reason I think this is a problem is I run other Linux systems and I normally
only see this when copying a large file (just so you know why I consider this a problem).

I've done multiple searches for information and found advice from "killing Hal/Hald" to
"Messing with 'hdparm'" and even "setting 'noatime' in fstab", and none of these
have worked the way ***I*** have tried them (just so I have covered as many of the search results as I can).

Does anyone have any advice? : )

Thanks!

Stratis

---

### Post by gdi2k on 2007-07-27
Hi Stratis, 

Ubuntu runs a daily "updatedb", which indexes all files on the hard drive so you can search for stuff quicker using the "locate" command. When you find your disk churning, open your System Monitor (System -> Administration -> System Monitor), click on the "Processes" tab and see if you can spot "updatedb". If so, that's probably the problem. You can disable this daily run, search the forums for "updatedb".

If not, there must be something else going on - did you install Google Desktop or similar?

---

### Post by Stratis on 2007-07-27
> **gdi2k said:**
> Hi Stratis, 

Ubuntu runs a daily "updatedb", which indexes all files on the hard drive so you can search for stuff quicker using the "locate" command. When you find your disk churning, open your System Monitor (System -> Administration -> System Monitor), click on the "Processes" tab and see if you can spot "updatedb". If so, that's probably the problem. You can disable this daily run, search the forums for "updatedb".

If not, there must be something else going on - did you install Google Desktop or similar?

Hello! : )

I know about 'updatedb', and I also know it would not need to run for 6+ hours. ; )

I had no idea Google Desktop was available for Linux.

---

### Post by RedSquirrel on 2007-07-27
How much RAM do you have? Is it possible that the system is moving things between RAM and disk on a regular basis? And watch the processes that are running with 'top'.

---

### Post by Stratis on 2007-07-27
> **RedSquirrel said:**
> How much RAM do you have? Is it possible that the system is moving things between RAM and disk on a regular basis? And watch the processes that are running with 'top'.

Using 224.2Mb out of 503.7Mb (as reported by the System Monitor program)
with 500Mb of swap.

I would like to be able to look at `top' and see something else, but all I ever
see is `Xorg' using the most CPU/MEM and on down the list.

If somebody could advise me of a quick and accurate way to find 
the process(s) doing this I would have no problem looking 
for a way to throttle it (them). : )

---

### Post by Stratis on 2007-07-28
Bump for more views. : )

If Ubuntu is running, the hard drive is ALWAYS active...

---

### Post by Stratis on 2007-08-20
Bump for new information:

I have 'System Monitor' running in a panel, and there is zero hard drive activity.

My hard drive LED is just always lit. 

Does anyone know what the issue could be?

---

