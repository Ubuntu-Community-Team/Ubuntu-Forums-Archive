---
title: "mdadm raid1 stops to work after kernel panic"
date: 2008-05-04
forum: General Help
---

### Post by Man of Wax on 2008-05-04
Accidentally I've booted with wrong grub parameters and my systems hanged with a kernel panic. After reboot my /dev/md2 device (raid1) stopped to work.
These are some logs:

```

wax@persifae:~$cat /proc/mdstat 
Personalities : [raid1] 
md2 : inactive sda1[0](S)
      293049600 blocks
       
md1 : active raid1 sdc6[0] sdb2[1]
      152264000 blocks [2/2] [UU]
      
md0 : active raid1 sdb1[1] sdc5[0]
      7815488 blocks [2/2] [UU]
      
unused devices: <none>

```

```

wax@persifae:~$sudo mdadm -Q /dev/md2
/dev/md2: is an md device which is not active

```

```

wax@persifae:~$sudo mdadm --assemble --scan /dev/md2
mdadm: failed to add /dev/sdc1 to /dev/md2: Invalid argument
mdadm: /dev/md2 assembled from 0 drives - not enough to start the array.

```

```

wax@persifae:~$cat /etc/mdadm.conf
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=2a37b0a1:4b6b28fc:0209446b:c3b28f2a
ARRAY /dev/md1 level=raid1 num-devices=2 UUID=19c49c5d:e3193aa1:657f267b:b23c2dee
ARRAY /dev/md2 level=raid1 num-devices=2 UUID=62a5cb51:36ca61a3:1298e6c2:30fde3ba

```

Thanks in advance for your help

---

