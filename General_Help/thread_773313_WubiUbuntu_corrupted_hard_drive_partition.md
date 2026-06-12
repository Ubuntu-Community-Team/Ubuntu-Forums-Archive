---
title: "Wubi/Ubuntu corrupted hard drive partition?"
date: 2008-04-28
forum: General Help
---

### Post by darkxman on 2008-04-28
Okay, I have 4 hard drives in my system. No problems... I decide to give Ubuntu 8.04 LTS a try with the Wubi on the official cd. 

Wubi installs fine. I reboot into Linux. Play around with it all day. Check to see if it can access my other NTFS formatted hard drives. Everything seems okay. 

I get tired, and I reboot to go back to Windows. Then Chkdsk starts up and then starts spitting a bunch out a bunch of errors about one of the partitions on one of my hard drives. Orphan files.... replacing invalid security ids... etc.. This goes on for about 15 minutes. When Windows finally starts up, about 20 GB of data is gone from the hard drive partition. All my other partitions and hard drives were fine. Very strange, because other than looking at the root directory of the partition, I didn't read any files on the drive or write any files to the drive while in Ubuntu. Also, I didn't have Wubi install Ubuntu to that partition.

Coincidence, bad luck, failing hard drive, Wubi bug, Ubuntu bug? I don't know, but I'm curious to know if this has happened to anyone else. Wubi worked perfectly, but after that I quickly uninstalled it and took the hard drive with the lost data out of my system. Might get brave enough to try it again on another major release.

---

### Post by Knighthammer on 2008-04-29
This is interesting - I got the live CD to work fine, thought I would install with wubi and it wouldn't go. Now I can't boot back into window and got a corrupted hard drive. Can't say the two are 100% related, but it does seem interesting that your having a similar issue. 
Best of luck to you - I'm reinstalling Windows next...then give it another try.

---

### Post by Gilean on 2008-04-29
Ago SAME FOR ME...before the final i had no problems using wubi. Just today i uninstalled the RC and installed the final by wubi. The installation went fine, but after rebooting, linux ubuntu desn't start (after the count down) and it says that the there's no partition to run ubuntu with.....plz help, i have not ubuntu now :(

---

### Post by ago on 2008-04-29
> **darkxman said:**
> Also, I didn't have Wubi install Ubuntu to that partition.
Well in this case it has certainly nothing to do with wubi, might also be a hardware failure. Did you hard reboot at all?

---

### Post by ago on 2008-04-29
> **Gilean said:**
> Ago SAME FOR ME...before the final i had no problems using wubi. Just today i uninstalled the RC and installed the final by wubi. The installation went fine, but after rebooting, linux ubuntu desn't start (after the count down) and it says that the there's no partition to run ubuntu with.....plz help, i have not ubuntu now :(
That is a very different issue from parent... In any case running chkdsk /r from windows is always commendable. If you have multiple disks see the WubiGuide under error 21.

---

### Post by Gilean on 2008-04-29
where's the wubi guide?

---

### Post by ago on 2008-04-29
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by darkxman on 2008-04-30
> **ago said:**
> Well in this case it has certainly nothing to do with wubi, might also be a hardware failure. Did you hard reboot at all?No hard reboot. Just a regular reboot from Ubuntu menu. Might just be a plain old hardware failure. Already took the drive out just to be safe. Hell of a coincidence...

---

### Post by ago on 2008-04-30
Pls let me know if you find out more

---

### Post by creampiggy on 2008-05-04
EXACTLY the same problem on my laptop!!! And my HDD is a Seagate 160gb less than one month old...

I installed Ubuntu with Wubi. When I use CHKDSK, a lot of files that are recently created under XP is said to be corrupted. But the older files are fine. I happen to have sfv checksum kept for most of my files, so I know which ones are corrupted.

Anyone knows what is wrong and how to prevent this?

---

### Post by creampiggy on 2008-05-04
BTW, I'm perfectly sure that I've NEVER hard rebooted.

---

### Post by creampiggy on 2008-05-04
UPDATE: After running CHKDSK /r surface check on an 100gb partition over the night, it's reported that around 20gb are bad sectors!! However, when I check HDtune, the Reallocated Sector Count is still 0...

I also used the Error scan of HDtune before using surface check CHKDSK /r, no error was found.

Anyone has any idea what's caussing the trouble?

---

### Post by creampiggy on 2008-05-05
I found out that it may have something to do with the BIOS hdd 137GB limitation. It seems XP can handle my 160gb hdd, even though the BIOS doesn't support it. But I guess Wubi get confused and cause the file system corrupted. If I'm correct, is it possible to improve Wubi?

BTW, My laptop is a 3 yr old compaq B3800.

---

### Post by ago on 2008-05-05
> **creampiggy said:**
> I found out that it may have something to do with the BIOS hdd 137GB limitation. It seems XP can handle my 160gb hdd, even though the BIOS doesn't support it. But I guess Wubi get confused and cause the file system corrupted. If I'm correct, is it possible to improve Wubi?

BTW, My laptop is a 3 yr old compaq B3800.

That I am aware of the 137GB should only affect the bootloader but once you have booted that should have no effect. I did a quick googling for [http://www.google.com/search?q=137-GB+ntfs-3g](http://www.google.com/search?q=137-GB+ntfs-3g) but could not find much to support the claim. I am interessed though in this thread, so if you find confirmation for any issue post it here or in launchpad and it will be addressed. The bad sectors reported by chkdsk are a good starting point.

---

