---
title: "recurring hard drive corruption all of a sudden on two different computers!"
date: 2021-08-01
forum: General Help
---

### Post by rebeltaz on 2021-08-01
My girlfriend's laptop, running Ubuntu 18.04 LTS has been acting odd - signing her out of skype and refusing to log back in; failing to update weather log files; etc - so we have to reboot it. When we do, it loads the grub menu, but once that disappears, it never goes any further. It just sits there at a blank screen, Ubuntu colored, but no logo. Eventually, we have to power it down manually and turn it back on. Every time, we get this error message.

```

/dev/sda1 contains a file system with errors, check forced.
/dev/sda1:
Inodes that were part of a corrupted orphan linked list found.

/dev/sda1: UNEXPECTED INCONSISTENCY: RUN fsck MANUALLY.
      (i.e. without -a or -p options)
fsck exited with status code 4
The root filesystem on /dev/sda1 requires a manual fsck

BusyBox v1.27.2 (Ubuntu 1:1.27.2-2ubuntu3.3) built-in shell (ash)
ENter 'help' for a list of built-in commands.

(initramfs)

```

To get the laptop back up and running, I have to boot to a live USB, manually run fsck, fixing the issues it finds and then rebooting. It works fine for a couple to a few hours then, does it again. 

I would assume a hard drive failing, **except**... My laptop is doing the **EXACT** same thing now. Both running Ubuntu 18.04, but two different manufacturers - both the laptops and the hard drives (mine is actually an ssd; hers is a physical drive) - yet we are both experiencing the exact same issues starting on the exact same day!

Is it possible something in an update could have caused this? If not, any other ideas on what I can look for? Any other information you might need, just ask...

---

### Post by Topsiho on 2021-08-01
Reading your text it appears to me that the fault is not your laptops, so it must be your Ubuntu's which is just the opposite thing I always think first.
Your suggestion it might be a faulty update might be on spot. If so, probably more people have had this update, and this issue, and might respond here. You could try whether another update resolves your problems. I have experienced this a few times myself (not often, 2 times or so since Dapper in 2006).

As your computer starts from a live USB-stick, this makes it more probable.

If another update does not help (soon enough) you might try whether a new install (with 20.04?) might help.

My two pennies, I wish you luck.

Topsiho

---

### Post by Impavidus on 2021-08-02
It looks like you experience some I/O error on hard drive access, which causes the filesystem to be remounted in read-only mode. That causes applications to fail. Then you reboot and find filesystem corruption.

Normally, this sounds like a hard drive problem, but with this happening on two computers at the same time, that's unlikely. Not impossible though, maybe vibrations at your place have just the right frequency to shake loose the hard drive connectors. Check them anyway. Overheating is another possibility. Are you using your computers in an exceptionally hot or dusty environment?

If this is caused by an update, I expect more people with the same problem. But 18.04 is a bit older and less commonly used (except, maybe, on servers). And maybe this is triggered by a package less commonly installed, but installed on both of your computers. Maybe you can find a package that was upgraded on both computers just before this problem arose. You can find the upgrades in the log files:```
grep " upgrade " /var/log/dpkg.log
grep " upgrade " /var/log/dpkg.log.1
```

Filesystem damage must happen at quite a deep level in your system. This is not a faulty application, as applications never access the hard drive directly. A bug in an application can damage a file, but not a filesystem. So if this is a bug, it must be in a filesystem driver or something like that. Have you done anything peculiar with the partitioning of the harddrives? Using LVM, RAID, any filesystems other than ext4?

---

### Post by Topsiho on 2021-08-02
It seems that my wife's laptop, running Ubuntu 18.04 too, has trouble with the latest installed kernel, numbered 151-generic. It refuses to halt in the normal manner, having to be forced to do so, and with determination too.
In  /var/crash are several crash reports, none of them the same, during the last week.
I now have it start from the previous kernel, 147-generic, and am hoping for the best.
I guess many computers still run with Ubuntu 18.04, as it runs (usually) quite well, so no reason to upgrade yet.

Had to report this, in my previous post there was no reason yet.

Topsiho

---

### Post by rebeltaz on 2021-08-02
> **Topsiho said:**
> It seems that my wife's laptop, running Ubuntu 18.04 too, has trouble with the latest installed kernel, numbered 151-generic. It refuses to halt in the normal manner, having to be forced to do so, and with determination too.
In  /var/crash are several crash reports, none of them the same, during the last week.
I now have it start from the previous kernel, 147-generic, and am hoping for the best.
I guess many computers still run with Ubuntu 18.04, as it runs (usually) quite well, so no reason to upgrade yet.

Had to report this, in my previous post there was no reason yet.

Topsiho

Now that you mention it... I do remember hers coming up with the "system has detected an error message - report?" box when it comes up and that MAY be after we've had to shut it down for the same reason you mentioned. I forgot about that!

I'll have to check those logs myself when I get home.

---

### Post by rebeltaz on 2021-08-03
> **Impavidus said:**
> It looks like you experience some I/O error on hard drive access, which causes the filesystem to be remounted in read-only mode. That causes applications to fail. Then you reboot and find filesystem corruption.

Normally, this sounds like a hard drive problem, but with this happening on two computers at the same time, that's unlikely. Not impossible though, maybe vibrations at your place have just the right frequency to shake loose the hard drive connectors. Check them anyway. Overheating is another possibility. Are you using your computers in an exceptionally hot or dusty environment?

If this is caused by an update, I expect more people with the same problem. But 18.04 is a bit older and less commonly used (except, maybe, on servers). And maybe this is triggered by a package less commonly installed, but installed on both of your computers. Maybe you can find a package that was upgraded on both computers just before this problem arose. You can find the upgrades in the log files:```
grep " upgrade " /var/log/dpkg.log
grep " upgrade " /var/log/dpkg.log.1
```

Filesystem damage must happen at quite a deep level in your system. This is not a faulty application, as applications never access the hard drive directly. A bug in an application can damage a file, but not a filesystem. So if this is a bug, it must be in a filesystem driver or something like that. Have you done anything peculiar with the partitioning of the harddrives? Using LVM, RAID, any filesystems other than ext4?

No... my file system is pretty standard ext4. It is hotter than Hades here right now, but no hotter than usual. This all seems to start just suddenly on both systems. I don't think there are any packages installed on hers at all that don't come built in. So that shouldn't be it...

---

### Post by rebeltaz on 2021-08-03
> **Topsiho said:**
> It seems that my wife's laptop, running Ubuntu 18.04 too, has trouble with the latest installed kernel, numbered 151-generic. It refuses to halt in the normal manner, having to be forced to do so, and with determination too.
In  /var/crash are several crash reports, none of them the same, during the last week.
I now have it start from the previous kernel, 147-generic, and am hoping for the best.
I guess many computers still run with Ubuntu 18.04, as it runs (usually) quite well, so no reason to upgrade yet.

Had to report this, in my previous post there was no reason yet.

Topsiho

Now my system is just freezing randomly. I can see that the temperature isn't overheating, so that's not it. I do see that my kernel is the same 151-generic as yours. How did you force it to run the 147? Maybe I'll try that...

---

### Post by Topsiho on 2021-08-03
Quite easy: choose the other kernel from the grub menu if it is visible when booting the computer.
If it is hidden (not visible) press Shift several times when booting (Legacy) or Esc (Uefi).
You'll probably have to try this a few times (to get the knack of it).
To make the grub menu not hidden at boot you'll have to change (as root, using sudo) the file  /etc/default/grub.
There is a line

GRUB_TIMEOUT_STYLE=hidden

in which hidden should be changed to menu

After saving this file you should do

sudo update-grub

and try and restart your computer.

This will show the menu at boot, and so you can select the other kernel, avoiding the 151 one.

Hope you have as much success as I did.

Probably, after the next update, you can revert (bring back)  /etc/default/grub to the old situation, just to make the computer as user friendly as possible.

Topsiho

---

### Post by rebeltaz on 2021-08-03
> **Topsiho said:**
> Quite easy: choose the other kernel from the grub menu if it is visible when booting the computer.




I'll try that now. Thank you. Hopefully this gets taken care of soon!

---

### Post by TheFu on 2021-08-03
Before assuming it is the kernel, I'd rule out bad hardware issues.  Besides having to systems with the same issue, I'd look at the HDD, SSD, and cables to those devices.  A bad update _could_ have happened, which would lead to something upstream - like the router/switch introducing corrupted files.

I'm running 18.04 and haven't seen kernel issues that weren't traced back to hardware problems. It is the HWE kernel:
```
$ uname -r
5.4.0-80-generic
```
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Ubuntu_18.04_LTS_-_Bionic_Beaver](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Ubuntu_18.04_LTS_-_Bionic_Beaver)

After you rule out the other hardware issues, only then would I look at software or corruption or kernel issues. Do the easy things first.  SMART data should be clear if the storage is having issues. Run long tests, then do a report.

If your storage has any odd components, say Intel Optane (or whatever they call it), then that would be important to note and search for issues around.

---

### Post by rebeltaz on 2021-08-03
> **TheFu said:**
> Before assuming it is the kernel, I'd rule out bad hardware issues.  Besides having to systems with the same issue, I'd look at the HDD, SSD, and cables to those devices.  A bad update _could_ have happened, which would lead to something upstream - like the router/switch introducing corrupted files.

I'm running 18.04 and haven't seen kernel issues that weren't traced back to hardware problems. It is the HWE kernel:
```
$ uname -r
5.4.0-80-generic
```
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Ubuntu_18.04_LTS_-_Bionic_Beaver](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Ubuntu_18.04_LTS_-_Bionic_Beaver)

After you rule out the other hardware issues, only then would I look at software or corruption or kernel issues. Do the easy things first.  SMART data should be clear if the storage is having issues. Run long tests, then do a report.

If your storage has any odd components, say Intel Optane (or whatever they call it), then that would be important to note and search for issues around.

SMART reports no issues. I'll let it do a test over night just to be sure, but... 

I don't know what Optane is, and I probably couldn't afford anything "odd". The hard drive in this laptop is just a Samsung 850 EVO SSD. I reckon that's normal enough? :) 

If it were JUST my computer throwing the same errors, I'd be more open to hardware issues (not that I will rule that out, though) but with two different computers both running different hardware with only the OS being common between the two... I just don't believe in coincidences. 

I'll report back on what SMART finds, though.

---

### Post by TheFu on 2021-08-03
Samsung 850 EVO had some issues a few years ago. A firmware update to the drive or bios was needed. Sorry, I don't recall which.

Also, check the system log files for errors and warnings. That could confirm the action in the kernel causing problems, RAM or some other issue.  A few weeks ago, I had to slow the RAM in my Ryzen box from 2800 Mhz to 2733 Mhz to prevent an page swap kernel trace/crash.  About a year ago, I had to reduce the RAM speed from 2966 to 2800 just to get a stable system after doubling the RAM.

---

### Post by rebeltaz on 2021-08-03
> **TheFu said:**
> Samsung 850 EVO had some issues a few years ago. A firmware update to the drive or bios was needed. Sorry, I don't recall which.

Also, check the system log files for errors and warnings. That could confirm the action in the kernel causing problems, RAM or some other issue.  A few weeks ago, I had to slow the RAM in my Ryzen box from 2800 Mhz to 2733 Mhz to prevent an page swap kernel trace/crash.  About a year ago, I had to reduce the RAM speed from 2966 to 2800 just to get a stable system after doubling the RAM.

I can look at the log files (actually I just took a look) but I have **NO** clue what I am looking at! I looked at syslog.1 (because that one was from yesterday when it actually locked up) and the only errors I see have to do with a video downloader I run.

---

### Post by TheFu on 2021-08-04
syslog is just 1 log file. There are others.  Check out **journalctl** to see the hardware logs. That command has all sorts of filter capabilities. Time, subsystem, errors are just some of the filters. Mine is setup to retain the last 10 boots of logs. I don't know what the default is.

---

### Post by Topsiho on 2021-08-04
TheFu is probably much more experienced than I am. Still I think it strange that the same problems exist on **two different computers**. Myself am always thinking of hardware problems rather than the Ubuntu software, but not this time.
I found crash reports in /var/crash, all very recent and with the same kernel. But also all different. On my wife's laptop (thus the third system here) with problems since  probably a week. And none for years before that. On my other systems, with ubuntu 20.04  /var/crash is empty.

So it is almost certain the kernel is at fault, this time. No need to test the hardware: disks, memory and such, in this special situation.
My wife now boots from another kernel and so far reports no problems.

So I think in this very special case pointing a finger to the kernel is not so strange.

Topsiho

---

### Post by dragonfly41 on 2021-08-04
Either point at a common factor such as kernel
or 
if malicious files are passed between these two devices
it might pay to check both devices as [documented here]("https://upcloud.com/community/tutorials/scan-ubuntu-server-malware/").

sudo rkhunter --checkall

sudo cat /var/log/rkhunter.log | grep -i warning

and possibly ... for deeper test ...

sudo apt-get install chkrootkit

---

### Post by rebeltaz on 2021-08-04
There seems to be another kernel available for upgrade (153) so... that might be a sign of issues with the previous one?

---

### Post by TheFu on 2021-08-04
> **rebeltaz said:**
> There seems to be another kernel available for upgrade (153) so... that might be a sign of issues with the previous one?

All software has issues.  It is highly unlikely that any specific fix will help you.  The changes for every new kernel are spelled out in the kernel changelog. This is public information.  Each week, a post of all Ubuntu updates is made to these forums, if you don't want to read from the actual changelog. I usually skim that list. I patch weekly, so it is clearer when an issue is related to patching or something else.  If my system starts behaving funny on a Tuesday, then it isn't from patching. I patch on Saturday mornings.

---

### Post by rebeltaz on 2021-08-08
> **TheFu said:**
> All software has issues.  It is highly unlikely that any specific fix will help you.  The changes for every new kernel are spelled out in the kernel changelog. This is public information.  Each week, a post of all Ubuntu updates is made to these forums, if you don't want to read from the actual changelog. I usually skim that list. I patch weekly, so it is clearer when an issue is related to patching or something else.  If my system starts behaving funny on a Tuesday, then it isn't from patching. I patch on Saturday mornings.

Be that as it may... all I can say is that since upgrading to a new kernel, neither computer has had a single issue since! I appreciate all of the help.

---

### Post by TheFu on 2021-08-08
> **rebeltaz said:**
> Be that as it may... all I can say is that since upgrading to a new kernel, neither computer has had a single issue since! I appreciate all of the help.

Being lucky is a good thing!  Happy you found the problem and the solution was available.  I have a few kernel issues which are known and unsolved since 2016.

---

### Post by Topsiho on 2021-08-09
Glad that the problem seems solved. Same on my wife's laptop. No issues since she uses an other kernel.
I am shocked it seems to be an Ubuntu software issue this time, as that (knock on wood) almost (almost!) never happens. But this time, on three different computers (that we know of) certainly pointed to the common kernel.
Happy hacking all of you,
Topsiho

---

