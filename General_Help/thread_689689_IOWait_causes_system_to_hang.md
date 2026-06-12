---
title: "IOWait causes system to hang"
date: 2008-02-06
forum: General Help
---

### Post by danbert on 2008-02-06
I am running Ubuntu 7.10 on my laptop and am having a very aggravating problem.  Every few seconds, the application I am using suddenly hangs and stops responding (turns grey with compiz on).  During this time, other applications seem to run fine unless I try to interact with them, and then they too start to hang.  This prevents me from using my system for long periods of time and my system is usable maybe 50% of the time.

Oddly enough, the problem seems to lessen if I have more applications running.  If I am just using firefox, usable time goes down to like 30% or less, but if I have Virtual Box and Matlab running, it goes up to around 80% productive.

I have used top and the system monitoring program, and all this shows that IOWait fills the processor time and sits around 98-99% for long periods of time before disappearing mysteriously.  I just can't seem to pin down what is causing the IOWait problem though...  It happens no matter what I do.

I have been doing some research to pin down the specific problem.  And it has to be a problem with Ubuntu.  This problem exists on every fresh install of Ubuntu since 6.06.  Ubuntu 6.06 does not have the problem.  I also tried a Mandriva install to determine if it was the linux kernel, but it did not have the IOWait problem either.

So now I am at an impass.  I don't know what else to try to diagnose the problem.  Does anyone know any other things I can do to pin down what is causing the IOWait?  Does some program tell you what the CPU is waiting on?  Is there some diagnostic tool I can run?  Are there other configurations I can try?  Any ideas would be appreciated.

---

### Post by danbert on 2008-02-06
Ok, I have been doing loads more research and have found some new possible solutions that haven't worked.  Some ideas were that the DVD drive cause the issues and I just flashed that with the latest firmware which many have said worked, and it did nothing.  Dmesg outputs this, which I believe is related.

```
[  544.744000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  544.744000] ata1.00: cmd ca/00:02:37:73:e2/00:00:00:00:00/e4 tag 0 cdb 0x1e data 1024 out
[  544.744000]          res 40/00:03:00:00:20/00:00:00:00:00/b0 Emask 0x4 (timeout)
[  544.744000] ata1: soft resetting port
```

---

### Post by Hal.9000 on 2008-02-08
I am having the same problem but for different reasons I believe.  Just about every time I turn on my computer IOWait uses 100% cpu for about 3-5 minutes and then mysteriously disappears.  I think in my case it is being caused by the computer trying to bring up a floppy drive of which I have none, this shows up in dmesg
```
[  578.617138] end_request: I/O error, dev fd0, sector 0 (shows up a couple times)

```
```
[  627.493327] Buffer I/O error on device fd0, logical block 0
[  639.696763] end_request: I/O error, dev fd0, sector 0 (then these repeat about 20 times)

```
I'm gonna make sure the floppy drive is disabled in bios but thats all I can think of doing.
PS My fstab doesnt have anything about fd0 in it, I think this is the nonexistent floppy drive but correct me if I'm wrong.

---

### Post by Hal.9000 on 2008-02-10
I realized that the floppy thing in dmesg has nothing to do with IOWait.  Although I did find that my problem is coming from anacron.
  I can reproduce this by typing```
sudo anacron -fn cron.daily
``` in a terminal.
Is it normal for anacron to cause IOWait to use 99% of my cpu time for a couple minutes?

---

### Post by dirk_k on 2008-03-20
I had the same problem with the high iowait:
- (very) slow disk access of files (copying files to /dev/null at around 10-15MB/s), but hdparm showed normal numbers (1150MB/s cached reads, 57MB/s buffered disk reads).
- slow starting of programs
- slow switching between programs: it seemed like I only had 256MB or so because it seemed like it was swapping or something, but there was hardly any disk access.
My system: AMD Athlon X2 @ 2.25GHz, 1GB (2x512, DDR2-800, CL4), 320GB SATA Seagate Barracuda 7200.10, Abit NF-M2 NView (onboard VGA, 64MB video memory)

I now am using the kernel from hardy and the system seems much more responsive!
So for all gutsy users having the high iowait problem try the upgrade. See for info on this:
[http://ubuntuforums.org/showthread.php?t=646755](http://ubuntuforums.org/showthread.php?t=646755)

Success.

---

