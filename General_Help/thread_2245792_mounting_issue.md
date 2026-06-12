---
title: "mounting issue"
date: 2014-09-26
forum: General Help
---

### Post by Apagon on 2014-09-26
On a usb key (appearing as /dev/sdd), I do (low level formatting): 
```

dd if=/dev/zero of=/dev/sdd1 
dd if=/dev/zero of=/dev/sdd2

```
then I re-format:
```

mkfs -t ext4 /dev/sdd   

```  
(Normally, we would have something like sddx, ```
mkfs -t ext4 -n 'LABEL' -I /dev/sddx
```, where x=1,2,...)
```

mount /dev/sdd /mnt 

``` -> ok no pb (df -h /mnt, I got all the usb volume, and can write on it.

but 
On an other linux machine, it 's not mounted, 
and not seen at all: 
```

blkid

```
-> see only my hdd partitions (sda)
my usb port is tested ok
```

ls -l /dev/disk/by-id/*usb*
-> ls: cannot access /dev/disk/by-id/*usb*: No such file or directory

```  
nothing happens on a windows machine as well
When I put it back on the machine I formated the key on, everything is ok !

---

### Post by Apagon on 2014-09-26
fdisk -l tells me that I erased partition table on the mbr (btw, fdisk -l sees my usb only on the computer I formatted the usb key on). I have tried to restore an mbr from another usb key (same model), in vain. 
If I havent killed the key because of numerous format operations, gpart should help me to restore the mbr. I havent got time to do this for now so I cannot tell you the result

---

