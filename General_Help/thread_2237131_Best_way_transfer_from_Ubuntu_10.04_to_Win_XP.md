---
title: "Best way transfer from Ubuntu 10.04 to Win XP?"
date: 2014-07-30
forum: General Help
---

### Post by pine508 on 2014-07-30
I have to transfer up to perhaps 10GB of stuff from a computer that has a WUBI-installed 64 bit Ubuntu 10.04 version on it.  The Windows 7 partition on it is completely unusable, so that's, unfortunately, all that is running on there.  However, there are a lot of files saved on the Windows side that I can see and get to from the Ubuntu side, and I'll need to get those to the target computer.  The target computer is a desktop running Windows XP with enough space on the hard drive to receive the files.

What I have:


[LIST]
[*]A home wireless router
[*]A crossover cable
[*]About a week to get this done
[*]A 4 GB flash drive.
[/LIST]

I tried installing Nitroshare on the Ubuntu computer to try to transfer the files wirelessly, but running the package installer failed with an error:

```
Error:  Dependency is not satisfiable: libc6 (>= 2.14)
```

So, **What would people suggest to get this done as quickly/painlessly as possible?**  

Thank you!

---

### Post by SuperFreak on 2014-07-30
So you want to transfer files from a PC with OS that is unsecure to a PC with an OS that is also unsecure(neither OS is presently supported nor receives security patches unless 10.04 is a server edition). What is the point of this. Why not delete XP and install Lubuntu on the PC and you should have no difficulty transfering files with the crossovercable. I suspect it will take far less than a day  depending on how much data is on the 10.04 PC

[https://help.ubuntu.com/community/Lubuntu/InstallingLubuntu]("https://help.ubuntu.com/community/Lubuntu/InstallingLubuntu")

also install SAMBA on both machines

---

### Post by pine508 on 2014-07-30
I might consider that at some point, but for now I want to just backup this computer and _get this stuff stored_, because I need to part with the Ubuntu computer next week.  Thanks.

---

### Post by SuperFreak on 2014-07-30
You have a flash drive. If both PCs have USB ports would you not be able to copy the files from one PC on the flash drive and then copy the from the flash drive to the other PC. I know you have more files on the first PC than can fit but do it in stages

---

### Post by pine508 on 2014-07-31
Thanks. Yes, that was my fall-back, but I just wanted to check if there were a more efficient/obvious way than via the flash drive.

---

### Post by dragonfly41 on 2014-07-31
I can think of several approaches ... given the timescale. But here is one for cloud backup.

Install Spideroak ([www.spideroak.com](www.spideroak.com)) on both Ubuntu 10.04 and your target computer for data backup to cloud.  Spideroak gives 2 GB free storage and you can buy in slugs of 100 GB at $10 per month if you prefer to keep a backup of your 10 GB.   But you should be able to use the Spideroak free 2 GB storage as a staging post to transfer data to your target computer in stages.

---

### Post by howefield on 2014-07-31
Think I would take the hard disk from the XP machine and hook it up to the Win 7 machine, transfer the files to it, and then put it back into the XP machine.

Or with a week to complete, buy a larger flash drive / backup drive :)

---

### Post by SuperFreak on 2014-07-31
> **howefield said:**
> Think I would take the hard disk from the XP machine and hook it up to the Win 7 machine, transfer the files to it, and then put it back into the XP machine.


+1

Here's another method without removing the HD
[http://www.liberiangeek.net/2010/11/enable-file-sharing-windows-xp-ubuntu-10-10-maverick-meerkat/]("http://www.liberiangeek.net/2010/11/enable-file-sharing-windows-xp-ubuntu-10-10-maverick-meerkat/")
But this will only work if you can use 10.04 on your WUBI...unlikely as you said Win 7 doesn't work

---

### Post by stalkingwolf on 2014-07-31
adrive has a free account that offers 50gb of storage as i recall

---

