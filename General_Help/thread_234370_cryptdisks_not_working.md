---
title: "cryptdisks not working"
date: 2006-08-11
forum: General Help
---

### Post by solsTiCe.dhiver on 2006-08-11
hi. 
i got a luks crypted partition on hda10. 
works on another distribution when i mount it manually. 

```
crpysetup luksOpen /dev/hda10 hda10
mount /dev/mapper/hda10 /mnt/p2p 
```

but on Dapper, /etc/init.d/cryptdisks says [OK] but hda10 is not mounted at all!

then when i attempt to mount it manually. i got an error:
```
cryptsetup luksOpen /dev/hda10 hda10 --key-file mdp_p2p
key slot 0 unlocked.
Command failed: device-mapper: create ioctl failed: Device or resource busy
```

i have found that /dev/mapper is filled with all my partition !!
it should only have control. but after i booted, i got hda1 , hda2 ,hda3,hda4,hda5,hda6,hda7,hda8,hda9,hda10 

ALL MY PARTITONS even though only hda10 is luks crypted. 

i tried:
```
cryptsetup luksClose hda10
Command failed.
```

but /dev/mapper/hda10 was gone 
and i could :
```
 cryptsetup luksOpen /dev/hda10 hda10 --key-file mdp_p2p
key slot 0 unlocked.
Command successful.
```

what is that mess ? 

```
cat /etc/crypttab
# <target name> <source device>         <key file>      <options>
hda10           /dev/hda10              /root/mdp_p2p   luks
```

```
cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults         0       0
/dev/hda1       none            swap    sw               0       0
/dev/hda8       /               reiserfs notail          0       1
/dev/hda2       /media/hda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0    1
/dev/hda5       /media/hda5     xfs     defaults         0       0
/dev/hda6       /media/hda6     reiserfs defaults        0       2
/dev/hda7       /media/hda7     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda9       /media/hda9     reiserfs defaults        0       2
/dev/mapper/hda10 /media/hda10  xfs     defaults         0       0


```

---

