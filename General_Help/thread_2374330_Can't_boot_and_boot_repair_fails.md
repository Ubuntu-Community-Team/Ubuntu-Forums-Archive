---
title: "Can't boot and boot repair fails"
date: 2017-10-14
forum: General Help
---

### Post by chssteakjedi on 2017-10-14
I have been running 16.04 for a number of weeks and decided to do a restart as I was having some issues accessing some of the processes running on the system (mainly Plex). Upon reboot, it immediately went to Grub2. I attempted to do some searches and came across some commands to run, but it always ended in an error attempting to read outside of hd0. I used a USB to boot into boot-repair and followed the prompts on there. It indicated it was successful and I got the lovely purple boot screen afterwards. I thought I was in luck, selected to boot Ubuntu and it again gave me the error of attempting to read outside of hd0. I pressed enter and it immediately went into kernel panic. 

I will admit that I'm a novice with all of this and I followed many guides to get my system up and running. Here is the pastebin from boot repair. Any help would be greatly appreciated so I don't lose multiple TB of data. Thanks in advance!

[http://paste.ubuntu.com/25738840/](http://paste.ubuntu.com/25738840/)

---

### Post by oldfred on 2017-10-15
What brand/model system?

Do you have drive set to AHCI, not IDE nor RAID?

Some older systems have issues booting from files located far from start of drive. Was limits with IDE type drives.
Linux locates files somewhat randomly anywhere on drive. So one time system may work, then on update if boot file is then further from start, it stops working.

Solution is to install with smaller / (root) partition and then large /home or /mnt/data partition for rest of drive.
I normally use 25GB for / and current install uses about 11GB of that, but all data is in a data partition, so /home is tiny. My /home is mostly the hidden user configuration files.

If AHCI already on, can you get to grub menu?
Since only one install, menu will not normally appear, you have to hold shift key from BIOS until it is shown.  But if grub menu too far from start that may not work either.
If you can get grub menu, then try an older kernel.

---

### Post by chssteakjedi on 2017-10-15
Right now I'm backing up files, so I can't get to the BIOS. The system is a HP Z600. Is there a good guide to follow so when I redo this I don't mess something up?

---

### Post by oldfred on 2017-10-15
Must be a pretty old work station.
Thread installing 10.10 back in 2010.
[https://ubuntuforums.org/showthread.php?t=1644437](https://ubuntuforums.org/showthread.php?t=1644437)

Do not know RAID, are you using RAID?
Some drivers may now be obsolete. 
If still issues I might try 14.04 or 14.04 server install.

---

