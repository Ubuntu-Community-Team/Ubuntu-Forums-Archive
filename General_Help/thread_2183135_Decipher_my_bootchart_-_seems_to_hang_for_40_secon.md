---
title: "Decipher my bootchart - seems to hang for 40 seconds"
date: 2013-10-23
forum: General Help
---

### Post by roger-grayson on 2013-10-23
I have a decent system with a quad core i7, 24GB RAM, and my OS on an SSD. This is a fairly fresh install of Ubuntu 13.10. The main change I have made is installing Gnome Shell and using that instead of Unity, but that shouldn't affect the boot process.


bootchart shows most everything completing in around 10 seconds, and then things sleep until almost 50 seconds. I'm looking for some help in deciphering the chart and fixing the issue. Many thanks in advance!


[IMG]https://lh4.googleusercontent.com/-Sg8TFaIWSws/UmgxHT8IX9I/AAAAAAAAfT4/OB2hUUi3SGk/s0/diablo-saucy-20131023-2.png[/IMG]

---

### Post by roger-grayson on 2013-10-28
Is this the wrong forum to post this, or is it that no one knows how to read bootchart? If I should post it somewhere else instead, please advise :)

---

### Post by roger-grayson on 2013-10-28
Apologize for talking to myself, but I believe this is more of a bootchart issue than an actual boot issue. I can actually reboot my machine, log into Gnome with 15 seconds, bring up the File Manager, navigate to /var/log/bootchart/, and then I have to wait for 20+ seconds until the actual bootchart .tgz and .png show up. 

So, new question: what triggers bootchart to stop collecting data?

---

### Post by oldfred on 2013-10-28
I do not know boot chart, but just look at log files. First I look at is dmesg and look for errors, long times between entries or repeated entries that then may work second or third time.

 gksudo gedit /var/log/dmesg

In verifing above command I used laptop. Normally have checked desktop and had no real issues, but I now see this:

[    1.892342] firewire_core: created device fw0: GUID 00080da0d15d3e31, S400
[   29.801732] Adding 3068376k swap on /dev/sda6.  Priority:-1 extents:1 across:3068376k

---

### Post by tgalati4 on 2013-10-28
As I understand, there is some preload/reshaping that happens with the latest versions of Ubuntu, so that over time the boot time will improve.  Be patient and keep the upgrades going then keep a log of boot times.  I think you will find that they will go down over time as the boot process optimizes itself.  It's possible that *bootchart* is in conflict with the optimization process, I would remove it and collect stopwatch data first.  Then if you have a problem after a dozen reboots, install *bootchart* and dig deeper.

The delay in writing the bootchart output might be due to loading JAVA or a lock on the /var/log due to other housekeeping--which is higher priority and probably more important.

As far as *dmesg*, it's generally good advice to investigate as many bootup errors as possible and try to eliminate them, but many errors are just kernel/hardware detection, and unless you recompile your kernel to remove all of those extra hardware checks (for hardware that you don't have), you might only save a few seconds.  The risk of breakage by recompiling your kernel is high.

---

### Post by roger-grayson on 2013-10-28
Thanks guys. I've decided this isn't a boot issue itself, but rather an issue with bootchart. I was previously booting and checking out the bootchart via ssh access. After examining the boot multiple times with a direct monitor, I've noticed its consistently less than 15 seconds.  I appreciate the feedback and suggestions!

---

