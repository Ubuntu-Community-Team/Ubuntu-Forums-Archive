---
title: "File system become read-only after some time"
date: 2020-04-05
forum: General Help
---

### Post by Will1134 on 2020-04-05
Hi all, hope you're all staying safe and making the best of the situation.

I'm having this problem with my Ubuntu 18.04 LTS that I don't know how to diagnose. What happens is after some time, often when the computer is unused but also in the middle of using it the filesystem seems to switch to read-only. I cannot save documents and some web pages stop working properly. There is no error that comes up when this happens and being unable to save is the only sign something has gone wrong.

Can anyone give me some guidance on things I can try to help find out what's wrong with the system?

Thanks very much in advance!

---

### Post by kesetyan on 2020-04-05
Hi Will,

You are not, by any chance, running your Ubuntu in a dual boot arrangement with Windows 10 are you?  Apparently Windows 10 updates can reset BIOS/UEFI fast startup to enabled when it had previously been disabled.  Fast startup being enabled can cause such problems, it seems.  If you do not have a dual boot arrangement, perhaps your BIOS/UEFI has Fast startup enabled anyway and this might be causing instability.  The following link is where I gleaned the information so you might like to look: [https://askubuntu.com/questions/917695/read-only-partition-dual-boot-win10?rq=1](https://askubuntu.com/questions/917695/read-only-partition-dual-boot-win10?rq=1).  Good luck.

---

### Post by CatKiller on 2020-04-05
> **Will1134 said:**
>  What happens is after some time, often when the computer is unused but also in the middle of using it the filesystem seems to switch to read-only.

This is standard behaviour when filesystem corruption is detected. Since you say that it's been happening a lot, I'd suspect drive failure. Back up anything important, run fsck and any other checks for drive integrity, but expect to be replacing the drive.

---

### Post by Impavidus on 2020-04-05
> **kesetyan said:**
> 
You are not, by any chance, running your Ubuntu in a dual boot arrangement with Windows 10 are you?  Apparently Windows 10 updates can reset BIOS/UEFI fast startup to enabled when it had previously been disabled.

That can happen, but it will only make the Windows partition read-only and it will only happen when you run Windows, not right in the middle of your Ubuntu session.

This sounds like a hardware problem. Check for loose connectors, a failing harddrive, even overheating can cause this.

---

### Post by lvm on 2020-04-05
If anything goes wrong the first thing to check is /var/log/syslog. Could be a bit of problem if root filesystem becomes read-only though, but in this case running dmesg might help.

---

### Post by Will1134 on 2020-04-05
Thanks for the help so far. When CatKiller mentioned filesystem corruption I started copying files to a new drive (rsync). /home is already on a separate drive so I'm going to move all files than change that to being my /home location (which I think I've done before)

Also, no Windows on this computer. Connections seem fine and the drive was cool.

Thanks again, that might have saved a serious problem.

---

