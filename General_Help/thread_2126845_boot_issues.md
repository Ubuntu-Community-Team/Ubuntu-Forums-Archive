---
title: "boot issues"
date: 2013-03-18
forum: General Help
---

### Post by Fkemble on 2013-03-18
I made the mistake of installing plymouth without reading into it so I could change my splash. I also wanted to speed up my boot time (ubuntu 11.04 - amd e-300 1.3gz, 8 gigz of ram, 320 gb sata drive). Plymouth actually slowed it down and it's glitchy looking - so I disabled it. I installed bum and killed 2 or 3 services, I knocked off several unnecessary startup programs, I installed preload, I took out the quit splash line in my grub config file - now it's about a 45 second boot and takes about 20 seconds to log out between users. I've already wiped the thing probably 20 times in the last month with everything from fedora, mint, zorin, 3 versions of ubuntu, windows, etc. My wife is going to kill me if I wipe it again...lol  I would have used 12.04LTS but it hung up during the install, so I went back to 11.04 and classic gnome. I've only been a linux user for about a year and a half and not sure at this point what I can do to knock my boot speed back down to normal and reasonable time..I thought about clicking upgrade within update manager and hope it would rewrite the boot sequence (that way I don't wipe it clean again and my wife keeps her files..lol) .. what can I do?  (I'm also at work right now so I'm not behind the system)

---

### Post by cortman on 2013-03-18
11.04 loses support in another couple months. I would recommend you install the LTS, 12.04.
You should back up all your files before you reinstall so you don't lose any and so your wife doesn't get upset. Seriously, back your stuff up.
You have a 1.3 Ghz processor and 8 GB of RAM? Keep in mind with a processor that small your bootup time will take a bit with vanilla Ubuntu. In fact, I'd almost recommend a lighter version, such as Xubuntu, especially if you prefer a traditional desktop over Unity.
If the machine is crucial for day-to-day tasks, it's probably smarter to make yourself a virtual machine or get an old computer to play with and test things on rather than the main machine.

---

### Post by oldfred on 2013-03-18
Your 11.04 has expired, so you will not get any more security updates.
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

If you have a separate /home and/or separate /mnt/data partition(s) you can do a clean new install without losing any data. Plus you should be backing up /home anyway so you can always restore data.

With a laptop hard drive, a 40 sec boot is not bad. Those with really fast boot times have SSD. My BIOS to grub menu (mostly BIOS) takes 10 to 12 sec and my SSD (MicroCenter noname or slow for SSD) takes 10 sec to boot or total time of about 25 sec to boot.

       To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

      
 Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Link is on move home but see post by bodhi.zazen on data partition #6
[URL="http://ubuntuforums.org/showthread.php?t=325048"]http://ubuntuforums.org/showthread.php?t=325048

[/URL] Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

[URL="http://ubuntuforums.org/showthread.php?t=325048"]
[/URL]

---

### Post by Fkemble on 2013-03-18
Thank you for the suggestions. I wonder, if I run the 12.04 LTS live cd and click the upgrade option, if it will clear all my boot settings..? my only question then is if Plymouth is disabled during the upgrade, then it won't matter then it's still in the system right..?

---

### Post by cortman on 2013-03-18
Upgrading won't clean up the boot issue- you want a full reinstallation.
Thanks for pointing out the 11.04 actually IS EOL oldfred- I'd forgotten that that was before the 18 month standard.

---

