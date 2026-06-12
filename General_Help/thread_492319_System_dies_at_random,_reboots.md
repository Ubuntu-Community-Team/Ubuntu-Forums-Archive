---
title: "System dies at random, reboots"
date: 2007-07-04
forum: General Help
---

### Post by Mr. Picklesworth on 2007-07-04
I am running Ubuntu Feisty Fawn (7.04), kernel 2.6.20-16-generic, with the following hardware:

Processor: AMD Athlon(tm) XP 2500+, 1.8 gHz
RAM: 1265 MiB
Video: Radeon 9600 Pro
Audio: Soundblaster Audigy

I have tried using both the proprietary and OSS drivers for my video card, with no difference.

In a seemingly random manner, my system clicks off (instantly -- no shutdown process), and reboots. This does not happen with a Windows install on the same computer.
There is absolutely no slowdown or sign that I can see that the thing is about to die; one moment it's running fine and the next moment it is shut down / starting up again.

I'm a bit lost as to where I should look to get more information on what is going wrong, so maybe this is a known problem with a known fix? (Or can you help me find more information on what is happening?)


Here is /var/log/messages from what looks like between running and rebooting.```
Jul  4 11:37:37 mccall-desktop gconfd (dmccall-5484): starting (version 2.18.0.1), pid 5484 user 'dmccall'
Jul  4 11:37:37 mccall-desktop gconfd (dmccall-5484): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jul  4 11:37:37 mccall-desktop gconfd (dmccall-5484): Resolved address "xml:readwrite:/home/dmccall/.gconf" to a writable configuration source at position 1
Jul  4 11:37:37 mccall-desktop gconfd (dmccall-5484): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jul  4 11:37:37 mccall-desktop gconfd (dmccall-5484): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jul  4 11:37:37 mccall-desktop gconfd (dmccall-5484): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jul  4 11:37:44 mccall-desktop gconfd (dmccall-5484): Resolved address "xml:readwrite:/home/dmccall/.gconf" to a writable configuration source at position 0
Jul  4 11:44:12 mccall-desktop syslogd 1.4.1#20ubuntu4: restart.
Jul  4 11:56:53 mccall-desktop -- MARK --
Jul  4 12:16:54 mccall-desktop -- MARK --
Jul  4 12:25:33 mccall-desktop gconfd (root-8038): starting (version 2.18.0.1), pid 8038 user 'root'
Jul  4 12:25:33 mccall-desktop gconfd (root-8038): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jul  4 12:25:33 mccall-desktop gconfd (root-8038): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Jul  4 12:25:33 mccall-desktop gconfd (root-8038): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jul  4 12:25:33 mccall-desktop gconfd (root-8038): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jul  4 12:25:33 mccall-desktop gconfd (root-8038): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jul  4 12:26:03 mccall-desktop gconfd (root-8038): SIGHUP received, reloading all databases
Jul  4 12:26:03 mccall-desktop gconfd (root-8038): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jul  4 12:26:03 mccall-desktop gconfd (root-8038): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Jul  4 12:26:03 mccall-desktop gconfd (root-8038): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jul  4 12:26:03 mccall-desktop gconfd (root-8038): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jul  4 12:26:03 mccall-desktop gconfd (root-8038): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jul  4 12:26:03 mccall-desktop gconfd (root-8038): GConf server is not in use, shutting down.
Jul  4 12:26:03 mccall-desktop gconfd (root-8038): Exiting
Jul  4 12:33:25 mccall-desktop syslogd 1.4.1#20ubuntu4: restart.
Jul  4 12:33:25 mccall-desktop kernel: Inspecting /boot/System.map-2.6.20-16-generic
Jul  4 12:33:25 mccall-desktop kernel: Loaded 24977 symbols from /boot/System.map-2.6.20-16-generic.
Jul  4 12:33:25 mccall-desktop kernel: Symbols match kernel version 2.6.20.
Jul  4 12:33:25 mccall-desktop kernel: No module symbols loaded - kernel modules not enabled. 
Jul  4 12:33:25 mccall-desktop kernel: [    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007 (Ubuntu 2.6.20-16.29-generic)
```

Also, (this is edited in to the post, by the way), these threads look similar:
[http://ubuntuforums.org/showthread.php?t=378088](http://ubuntuforums.org/showthread.php?t=378088)
[http://ubuntuforums.org/showthread.php?t=275054](http://ubuntuforums.org/showthread.php?t=275054)
[http://ubuntuforums.org/showthread.php?t=269197](http://ubuntuforums.org/showthread.php?t=269197)

---

### Post by smoker on 2007-07-04
just a suggestion, i think even though you say the machine runs ok in windows, i think i would suspect either overheating or a faulty graphics card. if you can in your bios, check the temps next time it happens, or try using an app like 'mark3d' in windows to stress your pc and see it something similar happens in windows.

plus i would do a ramcheck also.

---

### Post by ubuntu.daemon on 2007-07-04
ya some of those links were about just the Xsession rebooting, but as smoker said it probably is the overheating honestly and ubuntu isnt keepping the processor or w/e at reg temp, so the bios resets?  lol i used to have that problem with ubuntu on my desktop, this a desktop or a laptop that your having problems with?  But again check your bios bc your problem might lay there in there,  whats are your specs anyways?

---

### Post by Mr. Picklesworth on 2007-07-04
Eek! I think you're right.
Unless sensors-applet is wrong, something in there (CPU, looks like) is 68°C!
Temperature is going down steadily, but it doesn't look very happy. System monitor applet shows processor use at 5-10%, though previously it was about 100%. I will see how that relates here... Probably don't want to run this thing for very long.

Any fix I can apply to get Ubuntu to notice the high temperature and to make use of the many fans in this computer?

Edit:
60°C now. Decreasing steadily. Strange...

---

### Post by ubuntu.daemon on 2007-07-04
yeah i dont think the applet that was in there was reading temps/not high enuf fan speeds, but you put all 3 items where they need to go?  you could just be safe and put it on your runlvl for boot up but other than that i dont know what to tell you, besides look on the forums and see if anyone else with your laptop/brand has similar issues
GL:popcorn:

---

### Post by Mr. Picklesworth on 2007-07-04
Oh, right, this is a desktop by the way. Previously ran pretty well, around 40ish degrees if memory serves me right.

I guess I could open it up and see if all the fans are working, etc.

CPU temperature from that applet got down to around 50, but then spiked back to 63 as soon as I started watching a video via a Flash player.

---

### Post by smoker on 2007-07-04
>  I guess I could open it up and see if all the fans are working, etc.

dust can cause a lot of problems, if you've not had the cover off for a while, get a small paintbrush, or can of compressed air and clear any dust off fan blades and heatsink fins, though be careful and earth yourself (machine switched off obviously) (i know stating the basics, but someone may read this in future, lol.)

i fixed one that was overheating last week, the only problem was the pc case was positioned right against the side of the desk, and the panel vents were blocked, moving it an inch from the side of the desk allowed air to flow and cured the problem!

best of luck

---

### Post by Mr. Picklesworth on 2007-07-04
Heh... that's impressive. Shaved 20 degrees Celcius off the temperature with a little cleaning. Thanks for the suggestion; it probably saved a lot of money.
One of the fans was pretty heavily obstructed. Looks like most of the dust was flying at it, and the thing hadn't been cleaned in quite a while (I'm not a hardware person!)
This is an under the table computer, too, so I'll see if repositioning it helps.

It seems odd to me that running with Ubuntu the power would cut so frequently (for good reason) while with Windows it never did this, even with much more cpu-intensive stuff. Is Linux just more picky about CPU temperature by default, or is Windows being smarter about controlling temperature in this case?

---

### Post by smoker on 2007-07-04
> **Mr. Picklesworth said:**
> 
It seems odd to me that running with Ubuntu the power would cut so frequently (for good reason) while with Windows it never did this, even with much more cpu-intensive stuff. Is Linux just more picky about CPU temperature by default, or is Windows being smarter about controlling temperature in this case?

probably someone more knowledgable could explain the 'in's and out's', i think there is such a wide range of motherboards, cpus, bios configurations, that it would be hard to pin it down to a particular 'this or that'. suffice to say, if a machine (whatever os) suddenly begins cutting out, the first thing i look for is overheating!

anyway, glad it's running cooler, and hope that is problem solved;)

---

### Post by Mr. Picklesworth on 2007-07-09
Still unhappy with my CPU temperature. It starts off at a comfortable 35-40 degrees Celcius but creeps up to 66 (and eventually 70) rather quickly, with no visible attempt to reduce this temperature. (Even when it is idle, it takes a long while for the CPU temperature to go down at all). Maybe they're just really quiet fans, but they don't sound like they are doing much work, either.

Found a few things:
[https://launchpad.net/ubuntu/+bug/22336](https://launchpad.net/ubuntu/+bug/22336)
[http://ubuntuforums.org/showthread.php?t=478652&highlight=powernowd](http://ubuntuforums.org/showthread.php?t=478652&highlight=powernowd)

Eeek!:
```
dmccall@mccall-desktop:~$ sudo powernowd 
Password:
powernowd: PowerNow Daemon v0.97, (c) 2003-2006 John Clemens
powernowd: Found 1 scalable unit:  -- 1 'CPU' per scalable unit
/sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq: No such file or directory

PowerNowd encountered and error and could not start.
Please make sure that:
 - You are running a v2.6.7 kernel or later
 - That you have sysfs mounted /sys
 - That you have the core cpufreq and cpufreq-userspace
   modules loaded into your kernel
 - That you have the cpufreq driver for your cpu loaded,
   (for example: powernow-k7), and that it works. Check
   'dmesg' for errors.
If all of the above are true, and you still have problems,
please email the author: clemej@alum.rpi.edu

```

I also opened /proc/acpi/thermal_zone/THRM/trip_points:
```
critical (S5):           100 C
passive:                 100 C: tc1=4 tc2=3 tsp=60 devices=0xdf812338
active[0]:               100 C: devices=0xdf81e7d4

```
Unless I don't know what I am reading here... Critical, active and passive temperatures are all set to 100 C?! That definitely is well over the thing's critical temperature. (I believe it's around 75 C).
Can I just turn down one of those numbers to get Linux to regulate CPU temperature more aggressively?
Which one? What is Active and Passive CPU temperature? (My guess: Critical is the point where it forces a shutdown, Passive is the cpu temperature it goes for when the thing is not in use, and Active is what it aims for when in use?)

---

### Post by Wiebelhaus on 2007-07-09
Is the system on a battery [backup device]("http://www.apcc.com/products/family/index.cfm?id=21")?

[IMG]http://www.apcc.com/resource/images/family/primary/21_fam.jpg[/IMG]

---

### Post by Mr. Picklesworth on 2007-07-09
No, it is not. Just a regular surge protector.


Edit:

Nice! It actually cools down now.
If anyone else comes along this thread, there is an identical problem, with an answer, here:
[http://ubuntuforums.org/showthread.php?t=103262&highlight=powernowd+athlon](http://ubuntuforums.org/showthread.php?t=103262&highlight=powernowd+athlon)

I still wonder if I should change that trip_points file, though.

---

