---
title: "Feisty - High Load Performance Problems - Showstopper"
date: 2007-05-21
forum: General Help
---

### Post by JohnNichol on 2007-05-21
Hi, moved to Ubuntu Feisty (7.04) over the weekend and initial impressions are in the main really good. It installed well, I like the look and feel and when not loaded its pretty snappy, but ... when I put it under load it is dieing badly and the GUI stops responding.

Some more information. 

Running Feisty on a new IBM T60. Dual Core, 2GB ram. 
Eclipse 3.2.2, JDK 1.5.0_11.
4GB of swap allowed in a separate partition

I am loading the machine by running a number of Java processes including Eclipse which have large memory footprints. 

For a couple of minutes the load monitor tells me that the machine is running hard but everything seems to be responsive but then the machine will freeze, keyboard seems to be ignored, if I move the mouse the cursor will follow seconds or sometimes minutes later. The machine gives the impression of being dead, Alt-Ctrl-Fx doesn't work, as I say there appears to be no keyboard response. 

If I have the patience and leave the machine for a few minutes the desktop will sometimes return, without some of the applications and with my wireless network connection lost. 

I have googled and searched the forums but either haven't asked the right questions or have failed to find anyone with similar issues! 

Much as it loathes me to say it I am close to giving up on Ubuntu and returning to Windows XP, which also stuggles to handle the load, but does a better job than Feisty!!

Any help, suggestions, links greatly appreciated!! 

Regards, 

John

---

### Post by dexter on 2007-05-21
Does this only occur with eclipse ?
Does it happen with other java-based programs ?
Does it happen with non java-based programs ?

---

### Post by kalpik on 2007-05-21
Which java version do you have? Some people are having troubles with v1.6.. Try installing v1.5 :)

---

### Post by JohnNichol on 2007-05-21
> **dexter said:**
> Does this only occur with eclipse ?
Does it happen with other java-based programs ?
Does it happen with non java-based programs ?

It happens reliably when I put the system under a partular load pattern. Unfortunately this is the very load pattern I spent the weekend moving to Ubuntu in the hope of getting a more stable system. 

The load is produced by a collection of applications, mainly Java
Eclipse - up to 512MB
Swing GUI Client with a lot of event processing - 1024MB
Java Console application(s) - 1024MB
I also have Firefox, Thunderbird, Skype etc running

Using TOP or System Monitor I can see a number of processes with a lot of VM in use (as expected) and the CPU s are pretty busy (at around 100%) as expected. 

When the tipping point is reached X-windows will freeze and keyboard input seems be ignored. I can reliably reproduce the problem 100% of the time. 

My last crash was at 22:57 BST, some 15 minutes ago, this time the window manager has not returned at all. The clock on the machine is still showing 22:57 and top is still displayed with a load average of 7.47, 48 MB of memory free.

What might be interesting is the swap which is showing 

Swap: 0k total, 0k used, 0k free, 235888k cached - this has me wondering if something has gone wrong with my swap configuration. Time to power cycle the machine and see what swap says before it gets broken!!

John

---

### Post by JohnNichol on 2007-05-21
> **kalpik said:**
> Which java version do you have? Some people are having troubles with v1.6.. Try installing v1.5 :)
Using 1.5.0_11, the Sun version not GNU

---

### Post by ghell on 2007-05-21
You may have better performance with Sun Java 1.6. There have been quite a few performance upgrades as far as I know.

How much memory do you have, if you have under 2.5GiB but you are actively using 2.5GiB it will probably thrash like hell.

Are you sure you are definitely actually using Sun Java? Once you have installed it you must set it to default (of course check with java -version)

Are you able to lower the Java memory allocations by passing flags to the Java apps as you run them?

I have to ask, why do you have such large Java applications running? Is it just for load testing or something? I have only once ever written a Java application which required more than the default (32MiB?) and it was because the whole point in the app was to have an incredibly fast function that could check a database for duplicated ints (each possible int given a 1 bit flag gave it a 512MiB memory requirement but O(n) running time.)

Also are you running 64bit or not?

---

### Post by JohnNichol on 2007-05-21
> **ghell said:**
> You may have better performance with Sun Java 1.6. There have been quite a few performance upgrades as far as I know.
I am a Java developer and the project I am working on is a Java 1.5 one. 

> 
How much memory do you have, if you have under 2.5GiB but you are actively using 2.5GiB it will probably thrash like hell.

I have 2GiB physical but need to be able to deal with significantly more than 2GiB of application heap, so I am relying on the OS to swap for me. 

> 
Are you sure you are definitely actually using Sun Java? Once you have installed it you must set it to default (of course check with java -version)

Yes very sure. The way this is degrading isn't normal application degrade. 

> 
Are you able to lower the Java memory allocations by passing flags to the Java apps as you run them?
 
I could but then they wouldn't work as they need to address that memory and would give java.lang.OutOfMemory exceptions. 

> 
I have to ask, why do you have such large Java applications running? Is it just for load testing or something? I have only once ever written a Java application which required more than the default (32MiB?) and it was because the whole point in the app was to have an incredibly fast function that could check a database for duplicated ints (each possible int given a 1 bit flag gave it a 512MiB memory requirement but O(n) running time.)

I specialize in building high performance low latency Java applications for pricing and telecoms, so we are often needing to build large Java applications with heap sizes in Gigabytes. A lot of data to hold and a lot of real time events to process. 

> 
Also are you running 64bit or not?
32Bit.

The problem I am seeing pretty fundemtal and increasing I am thinking not Java related at all. 

I think I have problems with my swap settings and as a result an not able to address anything like the memory I expect. Off to google and explore somemore to understand how swap gets allocated and managed and see if I can fix things up. 

Really hope its something simple!! 

Cheers, 

John

---

### Post by JohnNichol on 2007-05-21
Ok, thanks for the help and suggestions guys, problem turned out to be very straightforward, although I have no idea how it happened. Basically my swap partition was not getting mounted. I followed instructions at [https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/66637]("https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/66637")
which helped to straighten out the problem and now my applications  are all running smoothly and happily eating into my swap space!

Should have worked this out myself earlier! But hey I am fairly new to Linux/Ubunto. NowI have the problem fixed Ubunto is responding way better than XP did under a similar load. Woohoo!!!

Cheers, 

J

---

### Post by psyke83 on 2007-05-21
> **JohnNichol said:**
> 
Swap: 0k total, 0k used, 0k free, 235888k cached - this has me wondering if something has gone wrong with my swap configuration. Time to power cycle the machine and see what swap says before it gets broken!!

By any chance, did you follow any "performance" guides that recommended tweaking the "vm.swappiness" attribute? Usually you save it to /etc/sysctl.conf. If you have, I recommend you remove that tweak; AFAIK setting it 0 eliminates swap usage entirely.

Regarding the system freezes, I have two recommendations:

1. Experiment with variations of the following parameters: noapic, nolapic, acpi=off
Edit /boot/grub/menu.lst and find the "defoptions=" line, editing it so it looks something like this (insertions in red):

```
# defoptions=quiet splash [COLOR="Red"]noapic nolapic acpi=off[/COLOR]
```

Run "sudo update-grub" and then reboot. If that helps, remove "acpi=off" and test again. If you still experience lockups, make sure to update your BIOS.

2. The next time you recover from a system freeze, it's very important to check your system logs, e.g.

```
dmesg | tail
```If in doubt how to troubleshoot any output, paste it here and maybe someone can help.

EDIT: Just saw your post regarding the solution, congratulations :). If you still experience any system freezes, however, the advice above is still relevant.

---

### Post by ghell on 2007-05-22
OK well even if your swap is working correctly, running high load (for example a lot of real time data to process) applications that require more memory than you actually have will cause a lot of page thrashing and this completely kills performance. If you have to use this much memory, it would be a very good idea to buy some more because you don't want to be in a situation where so much thrashing occurs. Your workplace may be able to help with the cost of this upgrade, as you need it for work.

Of course if the applications are big but low load, they may be able to live in swap for longer and not be constantly paged in and out for each other, which wouldn't be too bad. Really it depends what the applications are.

By the way you know you can just put 1.6 on and use -source and -target (or workspace/project options in eclipse) to compile for 1.5, is this not good enough?

---

