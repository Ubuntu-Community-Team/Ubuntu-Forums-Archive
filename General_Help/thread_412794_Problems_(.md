---
title: "Problems :("
date: 2007-04-18
forum: General Help
---

### Post by mrmonday on 2007-04-18
Hi all.

I will write all of my related (maybe) problems here.

Recently with the routine 30 boots fsck i get an error about root. It automatically restarts my PC before I can read it.

My PC freezes for no reason sometimes. Only the mouse responds. 

My PC restarts itself for no reason sometimes.

Recently I booted and got 

>  [17179605.440000] BUG: soft lockup detected on CPU#0!

I was left with a flashing dash. I rebooted and got the same. I rebooted again, and my PC crashed at the log on screen. I rebooted again and my PC crashed at the usplash (it does this often). I rebooted again and my PC crashed at the usplash. I rebooted again and now I'm here.

I have looked at my log files, and nothing seems unusual, and there seems to be no record of anything that could contribute. Please help, as this is becoming a pain now. Thanks.

---

### Post by newtonfn on 2007-04-18
I had a similar problem, my Pc said BUG: soft lockup detected on CPU#0! too

Unfortunately the cause of the error was a disk failure. Soon after ubuntu said that, windows began to failure too (i used to dual boot)

Result, I had to throw away that disk because i could never boot again after a while :(

---

### Post by mrmonday on 2007-04-18
My hard disk has already had a mini failure... I am looking for backup software at the moment - [see here -http://ubuntuforums.org/showthread.php?t=406919]("http://ubuntuforums.org/showthread.php?t=406919"). I hope this isn't the problem, as It will take me ages to put everything back. I have copied my critical data, but everything else will take months to get back. Are there any other possibilities?

Thanks.

---

### Post by strabes on 2007-04-18
sbackup is a great backup tool. If you want to schedule regular backups It uses cron jobs. It's in the repositories: ```
sudo apt-get install sbackup
```

---

### Post by sixstring on 2007-04-20
Hello, I am getting this error also installing 7.04.  I don't think it's a disk failure though because I can go back to 6.10 and everything works fine.  Windows also works fine.

I noticed an additional error when the kernel is booting, it says:
"BUG: timer is not connected to IO-ACPI"
which I'm guessing is a problem with time stamp from my AMD dual core CPU.  (i.e. Dual Core Optimizer software for Windows from AMD)

 my setup:
AMD64 X2 3800+
ATI x1900xt
2GB RAM

---

### Post by mrmonday on 2007-04-25
Something I have noticed, is that when my PC freezes, apparently for no reason, my network is loosing signal. Could this mean it is a problem with my wireless card drivers?

Is there a log file for my network? I can't find one :(

Thanks if you can help.

---

### Post by tgalati4 on 2007-04-25
It could also be whe wireless card failing itself.  I had an intermittent wireless card that would cause bus freezes.  Everything else seemed normal.  Since you are not seeing any messages in /var/log, I would suspect intermittent hardware.  Time to open up the machine, clean it out, reseat memory, etc.

Install smartmontools and look at the SMART errors on the disk (if any).  There are several good tutorials on the forum, search smartctl.

Boot from the rescue shell and do a short and long test:

smartctl -t short /dev/hda            (run the short test 1 or 2 min)
smartctl -l selftest /dev/hda        (show results on screen)
smartctl -t long /dev/hda             (run the long test, can take an hour)
smartctl -l selftest /dev/hda        (show results on the screen)

smartctl -a /dev/hda                     (show all SMART data about the drive)

Pay attention to the Power_On hours.  Anything over 20,000 hours gets exciting.

---

### Post by mrmonday on 2007-04-27
I have downloaded smartmontools from the repos, do I always use /dev/hda? will this scan all my partitons? Is there a way that I can dump the output to a file? Also, will I get a progress bar, or just a flashing line for a few hours?

Could this tool break my HDD if my HDD is nearits end?

Thanks.

---

