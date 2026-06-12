---
title: "Disk Sector Editor?"
date: 2007-05-02
forum: General Help
---

### Post by terces on 2007-05-02
Is there any kind of disk sector editor for Linux, either in the repositories or elsewhere?

I have a machine where I had a XP/Vista dual boot.  After the Vista install, (Vista sucks by the way), my XP installation which has always worked flawless was working kind of quirky.  I decided to reinstall XP; and when I did it made the Vista partition the system (C:) partition and the new XP install only the boot partition.  Needless to say this screwed some things up big time.  I backed up all my data to a RAID0 aray and proceeded to wipe the dedicated XP/Vista system files disk.  After I installed XP the backup RAID0 did not show up correctly but my other RAID0 for the programs did.  I messed around for hours trying to fix it and in the process converted it to a dynamic disk because I couldn't remember if the disk originally dynamic or basic.  That didn't work and seemed to make things worse so I converted the disk back to a basic disk by editing the third byte in line 01c0.  This worked and my disk was back to basic; a partition also showed up!  Unfortunately only one of two showed up and the one that did was my virtual machine partition which I did not care about as much.  Nothing I did could get that partition back, so I took the risk and edited line 01d0 to try and bring back the partition... well that didn't work and now I can't boot into Windows, use the Recovery Console, or anything if I have that disk hooked up to the motherboard.  So I'm hoping that Linux will let me boot with it but I'm in need of a disk editor so I can change the bytes back.

---

