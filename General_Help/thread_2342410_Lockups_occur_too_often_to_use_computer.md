---
title: "Lockups occur too often to use computer"
date: 2016-11-06
forum: General Help
---

### Post by yonnie on 2016-11-06
I have several computers that are low power quads and use the Bay Trail gpu chipset.  Every one of these computers have been doing random _lockups for over a year_.  I've read discussions that link updates to kernel 3.15? as when it started.  I moved from 12.04LTS to 14.04LTS and the lockups started, could not find a cure and thought it might be the computer.  I ordered a new one with pre-installed 16.04LTS and it started doing lockups within minutes of being turned on.

OK, can someone please tell me if anyone is addressing this problem?

Is there another chipset that works right that are used in a small form factor low power computer that does not have this lockup issue?

---

### Post by TheFu on 2016-11-07
How much RAM?
What size is the swap partition?
What does the workload look like?

When RAM (real and virtual) runs out, systems crash.

Normal system monitoring (which is commonly used by professionals) would provide this information.

---

### Post by yonnie on 2016-11-08
the HDD units are 4gb swaps and the ssd ones are not using swap.  ram is 4gb or 8gb, units lockup when browsing and/or libreoffice and/or just sitting there with no applications running.  They seem to lockup just because they can based on need.  The more you need it, the more they do it.  The special order one did it within 5 minutes after turn on, hadn't even connected to the network yet.

---

### Post by TheFu on 2016-11-08
Anything in the log files? HW issues?

When I had a similar issue with nothing HW reported in the log files, it was on a 2G RAM box with the default 2G swap.  Kept running out of RAM.  Made the swap 4G and never had the issue again.  If the swap truly is 4G, doubt that would help.

Check it with a **swapon -s** 
or** free -mh** cmds.

```
$ free -mh
              total        used        free      shared  buff/cache   available
Mem:           3.8G        2.6G        115M        642M        1.1G        290M
Swap:          3.9G        138M        3.8G

``` for example.

---

### Post by yonnie on 2016-11-08
which log files?

---

### Post by TheFu on 2016-11-08
> **yonnie said:**
> which log files?

Logfiles:
[https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles) and [https://askubuntu.com/questions/186276/where-are-all-the-major-log-files-located](https://askubuntu.com/questions/186276/where-are-all-the-major-log-files-located) explain.

---

### Post by bswarm2 on 2016-11-09
As per this [bug report]("https://bugzilla.kernel.org/show_bug.cgi?id=109051") on baytrail crashes with Linux, setting max_cstate=1 in the bios or grub should give you a rock steady system. If you can't set it in the bios, instructions [here]("http://askubuntu.com/questions/749349/how-to-set-intel-idle-max-cstate-1") for setting it in grub.

---

### Post by yonnie on 2016-11-09
That sounds like the band-aid I tried.  I did this a few days ago and the machine has not locked up once, yet.  This has been an annoying nuisance with 14.04 and 16.04 for over a year.  It used to be once in awhile whenever the cpu felt like it but after the 16.04 upgrade it became a daily event.  A setting that a user has to be aware of prior to installation is not a fix.  I doubt most users even know if their computer has a bay trail processor in it.  "Oh, crap the cpu is locked-up, what's wrong with it?"  Guess this thing called Linux is not reliable, is going to be their first and lasting impression.  Getting ambushed with lock-ups is not a good advertisement.  This problem needs to be addressed with a real fix.

---

### Post by alexjpowell on 2016-11-10
If RAM is not an issue maybe reduce swappiness down to 5-10

---

### Post by yonnie on 2016-11-14
> **alexjpowell said:**
> If RAM is not an issue maybe reduce swappiness down to 5-10
I have tried this in the past, did not work at all.  The suggestion from bswarm2 does seem to work, no more lockups from the zotac and Gigabyte computers.  I can't call this a fix as instead of addressing what appears to be a driver issue by altering the cstate condition.  Band-aid and helps no-one who just bought a Bay-Trail and certain graphics from applications still pause or act-up.  Not enough pressure has been applied to Intel to fix their issue.

---

