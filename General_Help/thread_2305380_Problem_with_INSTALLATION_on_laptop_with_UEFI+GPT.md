---
title: "Problem with INSTALLATION on laptop with UEFI+GPT"
date: 2015-12-05
forum: General Help
---

### Post by patryk8 on 2015-12-05
In the beginning, I want to apologize for my bad english :)
Ubuntu[14.04.3 - 14.10 - 15.04 - 15.10]
I have problem with installation Ubuntu on my new laptop as dual boot with Windows 10, i will try to explain every step which I did.
I bought new laptop Toshiba Satellite L50D-B-151 PSKULE, which have a UEFI firmware and GPT Partition Table. I upgraded system to Windows 10. When i want to install Ubuntu system via USB drive, I created a Ubuntu USB drive, i shrink my C drive, i turn off FAST START option in Windows and Boot Security in UEFI. 
I boot my pendrive as UEFI, firstly i tried to install Ubuntu 14.04, but when i was on step "Installation type" i choose something else and here problem started. Ubuntu installer (GParted) doesn't see my partitions, just see my disc 1TB as free space. So next what i did it was research for a solutions.
I found a few topics but anyone helped. 
I tried 'sudo gdisk -l /dev/sda' but my disk for sure has GTP Partition Table, and everything was ok. I tried to create partitions EXT3 via AOMEI Partition Assistant, but it still doesn't worked. 
Next I was trying to install Ubuntu 14.10, 15.04 and 15.10. In this versions, after running GParted I can see every partitions what i have. But when I tried to install Ubuntu and when i Click 'Next' button on third step 'Preparing to install Ubuntu' installation couldn't go to Installation Type, and error have shown as: "?? ????" - Yes there are question marks :x
--
ProblemType: Crash


Architecture: amd64


Date: Sat Dec  5 14:51:11 2015


DistroRelease: Ubuntu 15.10


ExecutablePath: /bin/parted_server


ExecutableTimestamp: 1445362669


ProcCmdline: parted_server


ProcCwd: /root
ProcEnviron:
 LC_COLLATE=C
 PATH=(custom, no user)
 LANG=en_US.UTF-8
 SHELL=/bin/bash
-- 



Maybe You have any solutions?

---

### Post by cariboo on 2015-12-05
First off, don't select install 3rd party software when doing an installation. 

I just installed the latest Xenial (16.04) on my Toshiba laptop with xero problems. If you can see the unallocated space as shown in your attachment, on you hard drive when you choose Something else, do your partitioning from there. It seems you are trying to make things more complicated than they actually are, by trying to setup the partitions before doing the installation.

---

### Post by patryk8 on 2015-12-05
Unfortunately, like i wrote before, installation stopped after shown error, and I can't start installation, it happened on 14.10, 15.04, 15.10 and i can check my partitions just in Gparted. But when i tried install 14.04, Gparted shown me nothing... just free space 1TB, but on 14.04 i could go to next step and select 'Something else' on instalation type, in contrast to 14.10, 15.04, 15.10, where before this step installation shown me error and it stopped.

---

### Post by patryk8 on 2015-12-07
Any ideas?

---

