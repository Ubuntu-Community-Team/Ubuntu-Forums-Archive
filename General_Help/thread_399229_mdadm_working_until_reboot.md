---
title: "mdadm working until reboot"
date: 2007-04-02
forum: General Help
---

### Post by cprophecy on 2007-04-02
hello I have managed to get my raid1 array up and running with mdadm. My only problem now is that I cannot seem to make it remain working after a reboot. Whenever i reboot, /dev/md0 totally disappears. The only way to get my array back is to run the command:

```
sudo mdadm --assemble --auto=yes /dev/md0 /dev/sda1 /dev/sdb1

```

This is my mdadm.conf:

```
DEVICE		partitions
ARRAY		/dev/md0 devices=/dev/sda1,/dev/sdb1 level=raid1 num-devices=2 UUID=497368ee:2605885f:7a03036a:f557219a
##CREATE	owner=root group=disk mode=0660 auto=yes
```

I've tried uncommenting the CREATE line
on the DEVICE line, instead of partitions i've tried using /dev/sda1 /dev/sdb1
on the ARRAY line i've tried it without the device=/dev/sda1,/dev/sdb1

I'm not sure what else I can do here. I dont know of any mdadm log so I'm just taking shots in the dark pretty much. Anyone know what I can do to make this array active after reboot? thanks.

---

