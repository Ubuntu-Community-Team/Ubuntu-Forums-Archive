---
title: "Unable to boot Ubuntu 16.04 after updates"
date: 2017-01-29
forum: General Help
---

### Post by oneboot on 2017-01-29
Hi there, 

I am new to all of this and I'm hoping that you can help. 

I have an older system that has a dual boot with windows xp. Windows xp hasn't been running for a while as (i believe) there is an issue connecting to the drive that it is on. 

I have been using 16.04 for a while. (It was upgraded from 13) It requested a restart after an auto update and now won't completly boot. instead, it gets hung up on the Ubuntu screen before it kicks me int emergency mode. 

So far I have: 
- attempted to start in advanced mode and attempted to fix the issue with all available options there. 
- reinstalled (updated?) grub from the grub menu. 
- re-installed grub using a boot repair disc (and followed all commands)
- reinstalled grub using a 16.04 live cd. 

None of the above have solved the problem. 

From the live CD I am able to run the trial and see and access all of my files. 

When selecting install on the Live CD it recognizes that I have 16.04 installed but only gives the option to overwrite the current install (not reinstall, keeping my files).

I'm at a loss at this point. I am not that familiar with all of this and would appreciate any help that you could provide. 

Thanks!

---

### Post by oldfred on 2017-01-29
May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by oneboot on 2017-01-29
I'll work on getting that for you. Will update when I have it. thanks!

---

### Post by oneboot on 2017-01-30
Ok, The BootInfo summary report can be found here:

[http://paste2.org/mgG7a12N](http://paste2.org/mgG7a12N)

Created it from the trial version running off the live CD.

Thanks again.

---

### Post by oldfred on 2017-01-31
Do not know anything about reiserfs.
Ubuntu's default is ext4. I might suggest using that for / and then if you want other formats use those for /home or /mnt/data partitions.

Your fstab shows a mount of Windows but you do not have that partition. Was that on another drive not shown?
That should not prevent booting, but may give errors when booting. Best to comment out from live installer for now.

You almost never install grub to a partition or PBR - partition boot sector. System cannot boot from that only from the MBR. Not sure if that interferes with your reiserfs, but with ext4 that space is not otherwise used, so not normally an issue.

Nothing else looks like an issue.

---

