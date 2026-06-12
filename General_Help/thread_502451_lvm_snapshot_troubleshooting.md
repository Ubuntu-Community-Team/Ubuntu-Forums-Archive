---
title: "lvm snapshot troubleshooting"
date: 2007-07-16
forum: General Help
---

### Post by gaebriel on 2007-07-16
Hi, I've been trying to create an LVM snapshot following directions on the [LVM Howto]("http://tldp.org/HOWTO/LVM-HOWTO/index.html") and on [howtoforge.com]("http://www.howtoforge.com/linux_lvm_snapshots") and have so far been unsuccessful with the three ubuntu 7.04 machines I've tried. I've tried just about every variation of the lvcreate -s/--snapshot command all to no avail. 

The basic command is: ```
sudo lvcreate -s -v -n systemsnapshot --size 20G /dev/vg1/system
```

OK. So now that I run the commands in another terminal I notice a little error at the beginning of the lvcreate output that says: "snapshot: Required device-mapper target(s) not detected in your kernel". Run an lsmod on the functioning debian4 box and I notice it has the dm_snapshot module loaded. A little `sudo modprobe dm_snapshot` action on my ubuntu boxes and I'm good to go. ```
sudo modprobe dm_snapshot
``` Why wasn't that loaded by default? I'm changing my post title from "can't create lvm snapshot" to 'lvm snapshot troubleshooting'. Hopefully this helps someone else out if they run into the same problem.

---

