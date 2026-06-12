---
title: "AMD Cool 'n Quiet in Sempron 3100+"
date: 2007-01-17
forum: General Help
---

### Post by raul_ on 2007-01-17
I have an AMD Sempron 3100+ (this one was unnecessary) and i tried to overclock it..and..well...it went wrong, i had to take the BIOS battery off so i could boot again. So i grabbed my motherboard manual #-o  and saw that it had a Cool 'n Quiet feature. I heard of it when I bought it but i never read about it. So i thought "cool, let me see what i can do with this" and all i could find was "If you're using Windows 2000"..."oh" i said..and then i read "Or" (my heart is pumping fast here) "If you're using Windows XP" (DARN!!!) . 

Ok...so i looked for it here in the forums and i saw some support for 64 bit processors, but I don't own an Athlon...how can i use this feature in Linux? Here is the output of powernowd:

```

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

what do I need to do? :-k

---

### Post by dcstar on 2007-01-17
> **raul_ said:**
> I have an AMD Sempron 3100+ (this one was unnecessary) and i tried to overclock it..and..well...it went wrong, i had to take the BIOS battery off so i could boot again. So i grabbed my motherboard manual #-o  and saw that it had a Cool 'n Quiet feature. I heard of it when I bought it but i never read about it. So i thought "cool, let me see what i can do with this" and all i could find was "If you're using Windows 2000"..."oh" i said..and then i read "Or" (my heart is pumping fast here) "If you're using Windows XP" (DARN!!!) . 
......
what do I need to do? :-k

There is an **athcool** package that you can try, it might work for later models of AMD CPUs.

---

### Post by raul_ on 2007-01-17
Isn't that an Athlon tool?

---

### Post by fragos on 2007-01-17
From a software perspect all AMD 64 bit processors are the same.  I would think athtool would work with your Sempron 3100+.

---

### Post by bettlebrox on 2007-01-17
U probably need to load the powernow_k8 or powernow_k7 modules, and the cpufreq & cpufreq-userspace modules:

 "That you have the core *cpufreq* and *cpufreq-userspace*
   modules loaded into your kernel
 - That you have the *cpufreq* driver for your cpu loaded,
   (for example: powernow-k7), and that it works. Check
   'dmesg' for errors."


If your not sure how to load the modules just ask! :)

---

### Post by raul_ on 2007-01-17
Update:

[http://www.ubuntuforums.org/showthread.php?p=2028746#post2028746]("http://www.ubuntuforums.org/showthread.php?p=2028746#post2028746")

:cool:

---

### Post by kerry_s on 2007-01-18
I hope that things not new, because your on you way to cooking it. ;) 
Athcool works best on AMD, you just install it and add the startup line to /etc/init.d/rc.local. I just put mine at the top, it will reduce the temp by 50%->

```
#! /bin/sh

athcool on &
sudo -u user firefox &
sudo -u user /usr/bin/firefox &
sudo -u user /usr/lib/firefox/firefox &


PATH=/sbin:/bin:/usr/sbin:/usr/bin
[ -f /etc/default/rcS ] && . /etc/default/rcS
. /lib/lsb/init-functions

do_start() {
	if [ -x /etc/rc.local ]; then
		log_begin_msg "Running local boot scripts (/etc/rc.local)"
		/etc/rc.local
		log_end_msg $?
	fi
}

case "$1" in
    start)
	do_start
        ;;
    restart|reload|force-reload)
        echo "Error: argument '$1' not supported" >&2
        exit 3
        ;;
    stop)
        ;;
    *)
        echo "Usage: $0 start|stop" >&2
        exit 3
        ;;
esac

```

---

### Post by Hubris2 on 2007-02-15
From my experience, the current kernels DO support Cool & Quiet...my system stays at 1Ghz, but scales to 2.2 as soon as I start glxgears..

> **bettlebrox said:**
> U probably need to load the powernow_k8 or powernow_k7 modules, and the cpufreq & cpufreq-userspace modules:

 "That you have the core *cpufreq* and *cpufreq-userspace*
   modules loaded into your kernel
 - That you have the *cpufreq* driver for your cpu loaded,
   (for example: powernow-k7), and that it works. Check
   'dmesg' for errors."


If your not sure how to load the modules just ask! :)

---

### Post by Hubris2 on 2007-02-15
Does anyone know if there is a manual way to control processor speed?  I'm discovering that while operating at 1Ghz is ok while I'm remote and network-limited, the time to spool up is annoying while I'm local.  It would be nice if I could issue a command and run the processor at full speed while I want, then let it idle down - but under my control.

---

