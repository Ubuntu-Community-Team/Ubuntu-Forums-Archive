---
title: "Bad sectors / blocks on HDD"
date: 2015-02-04
forum: General Help
---

### Post by sappy2 on 2015-02-04
Hey,

following problem: my windows vista frozens. Boot in safe mode doesnt work. Starting Ubuntu works temporarily but then it frozen to.
Starting Ubuntu 12.04 in advanced mode (Ubuntu, with Linux 3.13.0-44-generic recovery mode) leads to many error reports on screen, like:
> [sda] Unhandled sense code 
Sense Key: Medium Error [current] 
Add. Sense: Unrecovered read error - auto reallocate failed 
end_request: I/O error, dev sda, sector 551906160 
ata1: EH complete 
EXT4-fs error (device sda6): __ext4_get_inode_loc:3953: inode #2491629: block 9961582: comm init: unable to read itable block 
init: Failed to spawn startpar-bridge (friendly-recovery--stopped 
main process: unable to execute: Input/output error


Seem to be some defect sectors on HDD?


My system: Acer Aspire 8730G, Dual Boot System: Ubuntu 12.04 + Windows Vista, 32bit, GRUB Bootloader Version 2.02

Should i try a Ubuntu Live CD, and e2fsck, smartmontools or something like ntfsfix?


Kind Regards

---

### Post by Habitual on 2015-02-04
since it's a "EXT4-fs error" message, I'd suggest fsck'ing it using Live Media.
gparted has a Check function also, I believe.

I'd wait for someone else to chime in and have a gander at [https://help.ubuntu.com/community/FilesystemTroubleshooting](https://help.ubuntu.com/community/FilesystemTroubleshooting) while doing so.

---

### Post by Mark Phelps on 2015-02-04
Using ntfsfix is a waste of time since it only repairs the most trivial of NTFS problems and, in other cases, sets the "dirty" bit so Windows will run CHKDSK on it at next boot.  Reads to me like you have a hard disk that is already into final stages of failing outright.  Modern drives keep unused sectors aside so they can remap failing sectors to new ones -- but there is a limited supply.  From your error messages, it looks like there are no spares left.

You may be able to recover data from it using TestDisk or PhotoRec, but in cases of serious hardware failure, neither of those is going to do any good.

---

### Post by tgalati4 on 2015-02-04
Welcome to the forums sappy2.  You have a difficult situation.  I  would boot a LiveUSB or DVD and install *testdisk* during the Live session.  You need a wire to connect to the network, a free external disk or lots of USB sticks to capture the  data.  Don't shutdown, because *testdisk* will only exist in RAM and will disappear when you  reboot..

Open a terminal:

```
sudo apt-get install testdisk
```

Use *testdisk* to fix directories.  Then use Nautilus to move through your directory trees and recover data to your empty USB sticks.  You don't have much time, so prioritize your recovery.  If your directory structure is hopelessly messed up, then use *photorec* (which is part of *testdisk*) to recover individual files to massive directories (500 files are dumped into each directory).  The file names will be meaningless, but hopefully you will be able to open individual files.

Good luck, and be patient.

---

### Post by dragonfly41 on 2015-02-05
Further to the problem of sorting/managing photorec recovered files you can use the metadata in files.

Google search "photorec metadata"

[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)

[http://www.joshualyman.com/2011/05/using-photorec-and-a-bash-script-to-recover-51407-images/](http://www.joshualyman.com/2011/05/using-photorec-and-a-bash-script-to-recover-51407-images/)

---

