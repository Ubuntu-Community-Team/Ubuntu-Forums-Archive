---
title: "Suspicious sounds from computer"
date: 2021-03-20
forum: General Help
---

### Post by daanheuvelbeuk on 2021-03-20
My computer is starting to make suspicious sounds when running. I might have traced the source to my HD. Yesterday I ran badblocks which reported to bad blocks. 
```
me@Alfheim:~$ sudo badblocks -sv /dev/sda
Checking blocks 0 to 3907018583
Checking for bad blocks (read-only test):   0.00% done, 0:00 elapsed. (0/0/0 errdone                                                 
Pass completed, 0 bad blocks found. (0/0/0 errors)
```

I ran smartctl, but that seemed not to have started:
```
me@Alfheim:~$ sudo smartctl -l selftest /dev/sda
[sudo] password for me: 
smartctl 7.1 2019-12-30 r5022 [x86_64-linux-5.8.0-45-generic] (local build)
Copyright (C) 2002-19, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%      6760         -
# 2  Short offline       Completed without error       00%      6759         -
# 3  Short offline       Completed without error       00%      6759         -
```

Are there any other tools I can use to check the health of my HD?

---

### Post by Impavidus on 2021-03-20
First tell smartctl to run an actual check. I use```
sudo smartctl -t long /dev/sda
```
The check will take some time. On my hardware about an hour, but that's only a 320GB drive.
Then print the results of that test. I use```
sudo smartctl -a -d ata /dev/sda
```but the -d ata part is specific for my hardware. I can't say what additional options you may need.

---

### Post by grahammechanical on 2021-03-20
Ubuntu has Gnome Disks installed. Open Activities and search for Disks. That will tell you the health of hard drives. Open the Drive Options menu and select Smart data and self tests.

You might also want to check the fans to see if they are working correctly. The noise could be coming from the fans.

Regards

---

