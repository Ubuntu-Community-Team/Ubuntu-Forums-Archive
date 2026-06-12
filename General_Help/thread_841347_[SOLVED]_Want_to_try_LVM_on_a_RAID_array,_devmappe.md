---
title: "[SOLVED] Want to try LVM on a RAID array, /dev/mapper/control: open failed: Permissio"
date: 2008-06-26
forum: General Help
---

### Post by batfastad on 2008-06-26
Hi everyone
Messing around with Ubuntu Server 8.04 here and wanted to try using LVM with a large RAID device I've got installed.

I've installed lvm:
```
sudo apt-get install lvm2
```

Run lvm by just typing lvm at the prompt.

Then when I try lvm>lvcreate

I get the following error:
```
  /dev/mapper/control: open failed: Permission denied
  Failure to communicate with kernel device-mapper driver.
  /dev/mapper/control: open failed: Permission denied
  Failure to communicate with kernel device-mapper driver.
  Incompatible libdevmapper 1.02.20 (2007-06-15)(compat) and kernel driver 
  striped: Required device-mapper target(s) not detected in your kernel

```

I saw this topic: [http://ubuntuforums.org/showthread.php?t=689342](http://ubuntuforums.org/showthread.php?t=689342)
But when I type lsmod | grep dm_* as discussed I get exactly the same output as the poster expects.

Any ideas/suggestions?
I really want to give this a go as hopefully it will make the future management of my NAS RAID drive easier.

Thanks, B

EDIT: Solved, mod please delete.
I had to create the volume groups 1st, before I could do lvcreate... [http://www.tldp.org/HOWTO/LVM-HOWTO/index.html](http://www.tldp.org/HOWTO/LVM-HOWTO/index.html)

---

