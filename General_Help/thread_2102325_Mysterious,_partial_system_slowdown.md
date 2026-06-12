---
title: "Mysterious, partial system slowdown"
date: 2013-01-06
forum: General Help
---

### Post by ladasky on 2013-01-06
Hello everyone,

My system has started to experience very long delays.  Here's my configuration:

[LIST]
[*]Gigabyte GA-MA78-US2H motherboard, 8 GB RAM, AMD x6 1100T CPU
[*]NVidia 460 family GPU card
[*]Ubuntu 12.04.1 OS, 64-bit
[*]Two hard drives operated in RAID1 configuration, administered by *mdadm*: both Western Digital Caviar Black, one 640 GB, one 750 GB (see below)
[/LIST]

When an application starts, I will find myself waiting 30-60 seconds before the splash page even appears.  Thunderbird took close to three minutes to start.  When an application window finally opens, it will usually go gray for several seconds before returning control to the GUI.  When I access various menu options in the application, I will get similar long delays.  After I have exercised an application for a while, things seem to run normally, but the first several minutes are intolerably slow.  Furthermore, if I quit an application and restart it -- the second time through, it loads quickly.  

The system GUI is still very responsive, however, even if I'm waiting a long time for an individual application to execute.  That being said, I've noticed a much longer than usual pause between the login screen and the initial appearance of my desktop.

I have rebooted the system, and confirmed that the problem persists.

I have made some software and hardware changes recently -- some voluntary, some forced.  I have been operating a RAID1 for some time.  I _[had difficulty installing Ubuntu 12.04.1]("http://ubuntuforums.org/showthread.php?t=2090858")_ on it.  I eventually determined that this was due to one of the two hard drives in my RAID going gradually bad.  My BIOS was taking longer and longer to recognize one of my two hard drives at boot time, and eventually it stopped seeing the drive at all.

I RMA'ed the bad drive to Western Digital, as it was still under warranty.  But since they don't stock the 640 GB Black drives any more, they sent me a 750 GB Black drive as a replacement.  I did some reading before committing to using the mismatched drives in my RAID.  Since the drives had the same rotation speeds, the consensus was that RAID1 performance should be the same as it was with two hard drives of the same size.  I just have 110 GB of unused space on the larger hard drive.  In any case, things seemed to run smoothly for several boot cycles.  Now things are behaving oddly.

Software updates may be an issue.  Of course, Ubuntu is always sending me software updates, including kernel upgrades.  While running 11.10, I learned the hard way that certain combinations of the Linux kernel and NVidia's GPU drivers do not cooperate.  I _[remember seeing symptoms somewhat like I'm seeing now]("http://ubuntuforums.org/showthread.php?t=1960714")_ when I (and thousands of other users) had an NVidia GPU driver problem.  The problems I'm having are considerably less severe this time, though, so video driver issues may not be the cause.

If anyone has any suggestions as to how I might troubleshoot my problem, I would appreciate it.  Thanks!

---

### Post by HermanAB on 2013-01-07
First of all, think Linux, not Windows...

On a Linux system you can at all times see exactly what is going on using a few simple utilities:
$ sudo top
$ sudo ps -e
$ sudo dmesg
$ sudo tail -f /var/log/messages (or whatever log file you want to look at)

If find a process that is sitting there and using all resources, kill it.

You can also look at the DNS settings, since a lame DNS may also cause startup delays, but not this bad.

---

### Post by ladasky on 2013-01-07
> **HermanAB said:**
> First of all, think Linux, not Windows...

Trust me, I NEVER think Windows!  I've been with Ubuntu since v. 6.06.  I had plenty of experience with Unix from my college days in the 1980's.  (I used to write my term papers in **vi** and format them for printing with **ptroff**.  That doesn't mean that I'm an expert sysadmin by any means, though!)

I will check for a process that is hogging the CPU the next time I see a long delay.  While running **top** in a terminal window, I just tried starting a few applications I haven't executed since booting the machine.  I didn't notice any egregious CPU loading, but then again, the apps I tried came up within a few seconds.

I have to learn how to read the output of **dmesg**. I can see some errors there, but they don't seem to be time-stamped in any obvious way.  I don't know when they occurred.

---

### Post by ladasky on 2013-01-07
In the words of Lewis Carroll: "curiouser and curiouser!"

Today's boot and login sequence was quick.  All applications are now loading promptly.  I did nothing to the system!

Looking back over my previous posts, I've recently seen some similar behavior.  In my current system configuration, it would appear that _[certain performance issues may persist through two reboot cycles]("http://ubuntuforums.org/showpost.php?p=12393164&postcount=13")_ before they... fix themselves?

I can only guess as to why this might be.  Perhaps a kernel rebuild is being done on one reboot, but the corresponding GPU driver rebuild is not being done until the second reboot?  And when the system has rebuilt one but not the other, there are performance issues?

Any thoughts?  Thanks!

---

### Post by ladasky on 2013-01-09
Follow-up: I think I had a hardware problem, and I think that I just fixed it.  Marking as "solved."

After my last post, the problem came back.  Once again I experienced VERY long delays during the boot process, during the login, when new applications opened, even during shut-down.  As before, **top** showed no CPU loading worth mentioning.  I was certain that the Update Manager had not asked me to install any new software during the previous day's run.

In **dmesg**, I saw many ATA errors, notices about the system repeatedly applying a "workaround", and the occasional "interface fatal error".  I wanted to cut and paste my output to Ubuntu Forums for comment, but my system was so slow that I couldn't get my web browser running in 15 minutes!  My **dmesg** output resembled, but was not identical to, _[this]("http://ubuntuforums.org/showthread.php?t=1541210")_.

Then I remembered something that I had read a few years ago: _[SATA controllers on motherboards can fail]("http://www.tomshardware.com/forum/272503-30-faulty-board-sata-controller")_.  SATA cables also fail occasionally.  I bought two new SATA cables, and plugged my drives into two previously-unused SATA sockets.  ***ZOOM*** went my system.  Everything is running faster than it was when I deemed things were working acceptably!

[color="red"]NOTE to RAID users: problems with your RAID hardware may resemble a software problem.[/color]  Your system may still work, it will just be horribly crippled.

---

