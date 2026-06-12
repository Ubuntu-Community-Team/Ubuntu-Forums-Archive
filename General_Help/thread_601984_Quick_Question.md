---
title: "Quick Question"
date: 2007-11-03
forum: General Help
---

### Post by Arcleo on 2007-11-03
This question pertains to the relative health of my system.

Right now, all week I use Ubuntu as my main OS to do all my school work, programming, etc. However, on the weekends I like to play video games, when I have time, so I dual boot into my windows partition.

My question is, how much wear does this rebooting do to my hard drives just to change into a windows enviroment? The rest of the week, I just suspend my computer. Does suspending instead of powering off help at all with Hard Disk life?

Thank you for any suggestions.

---

### Post by nick_h on 2007-11-03
Suspending will power off your disk drive, so there is no difference in suspending and switching off.  I suppose that a reboot will cause more files to be read from the drive, but rebooting shouldn't cause significant extra wear on the drive.

---

### Post by Arcleo on 2007-11-03
Figured as much, just wanted verification.

Thanks.

---

### Post by nick_h on 2007-11-03
Here is some more info about HDD wear and tear which may be of interest to you.

You may have read some threads about Ubuntu killing your HDD.  There was a problem in Feisty where the HDD was not powered off in a nice way which resulted in the Power-Off Retract Count for the drive increasing on each shutdown.  This has been fixed in Gutsy.  You can check if you suffer from the problem by installing smartmontools,
```
sudo apt-get install smartmontools
```
and running.
```
sudo smartctl --device ata --attributes /dev/sda1
```
if the count doesn't increase on each reboot then you are OK.
Link - [Ubuntu is killing your hdd!](http://ubuntuforums.org/showthread.php?t=508576)

There is also an ongoing issue with the Load Cycle Count that you can check using the same tool.  There are a couple of useful posts [here](http://ubuntuforums.org/showpost.php?p=3675960&postcount=26) and [here](http://ubuntuforums.org/showpost.php?p=3675784&postcount=25).

---

### Post by Arcleo on 2007-11-04
Thanks a lot! I had downloaded smartmontools and using smartctl to check health status, but was having trouble deciphering the output.

Thanks again, have been a huge help! 

:)

---

