---
title: "How to remove stale LVM logical volumes/snapshots"
date: 2013-09-05
forum: General Help
---

### Post by adlerweb on 2013-09-05
Hello,

i'm currently experiencing a problem with LVM-strorage: I use a single VG called "storage" on a software raid to store virtual machines. I created snapshots some time ago and forgot to delete them, after the latest reboot i noticed the abandoned snapshots but can not remove them:

After booting all LVs are correctly identified, i get the corresponding device files in /dev/storage/ - as far as i can tell including all snapshots - and i can use lvdisplay/lvs to view LVs. However if i try to remove a snapshot using lvremove the command seems to get stuck - no messages on stdout/stderr and no possibility to stop the process using ctrl-c. If a remove-command is stuck all other lvm-binarys (including previously working lvdisplay/lvs) stop to work and also go into the mentioned stall. Even in this state i am still able to use/mount my LVs.

I noticed this behaviour also in the past on other systems - usually i delete the LVM and restore from backups but i would prefer to find a way to recover a lvm without recreating the whole storage.

Any ideas?

---

