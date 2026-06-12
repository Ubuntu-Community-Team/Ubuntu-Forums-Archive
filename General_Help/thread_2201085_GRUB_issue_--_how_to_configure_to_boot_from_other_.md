---
title: "GRUB issue -- how to configure to boot from other SSD drive"
date: 2014-01-22
forum: General Help
---

### Post by sergi-3 on 2014-01-22
Hello

I bought a new SSD drive with the idea of running my Ubuntu system on  it and leaving the other two SATA drives (which are configured in a RAID  array) for storage only.   Ubuntu installed with no problem, but it turns out that my  motherboard doesn't support AHCI and it doesn't see the SSD drive at all  -- so I can't configure it to boot from the SSD. 
  Can I, theoretically, install GRUB on the SATA array and configure it so it boots the SSD?


  When I run grub-mkconfig, it identifies the system installed in the SSD but it spits out the following error: 
  ```
### BEGIN /etc/grub.d/30_os-prober ###
ERROR: ddf1: seeking device "/dev/dm-2" to 18446744073709421056
ERROR: hpt37x: seeking device "/dev/dm-2" to 4608
ERROR: hpt45x: seeking device "/dev/dm-2" to 18446744073709547008
ERROR: isw: seeking device "/dev/dm-2" to 18446744073708469760
ERROR: sil: seeking device "/dev/dm-2" to 18446744073709289984
ERROR: ddf1: seeking device "/dev/dm-2" to 18446744073709421056
ERROR: hpt37x: seeking device "/dev/dm-2" to 4608
ERROR: hpt45x: seeking device "/dev/dm-2" to 18446744073709547008
ERROR: isw: seeking device "/dev/dm-2" to 18446744073708469760
ERROR: sil: seeking device "/dev/dm-2" to 18446744073709289984
ERROR: ddf1: seeking device "/dev/dm-2" to 18446744073709421056
ERROR: hpt37x: seeking device "/dev/dm-2" to 4608
ERROR: hpt45x: seeking device "/dev/dm-2" to 18446744073709547008
ERROR: isw: seeking device "/dev/dm-2" to 18446744073708469760
ERROR: sil: seeking device "/dev/dm-2" to 18446744073709289984
ERROR: ddf1: seeking device "/dev/dm-2" to 18446744073709421056
ERROR: hpt37x: seeking device "/dev/dm-2" to 4608
ERROR: hpt45x: seeking device "/dev/dm-2" to 18446744073709547008
ERROR: isw: seeking device "/dev/dm-2" to 18446744073708469760
ERROR: sil: seeking device "/dev/dm-2" to 18446744073709289984
Found Ubuntu 12.04.3 LTS (12.04) on /dev/sdc1
menuentry "Ubuntu, amb el Linux 3.8.0-29-generic (on /dev/sdc1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set=root 25ad7a52-d1b9-4d23-81b0-de24a593e8e5
    linux /boot/vmlinuz-3.8.0-29-generic root=UUID=25ad7a52-d1b9-4d23-81b0-de24a593e8e5 ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.8.0-29-generic
}
  
```Any help will be greatly appreciated... :)

---

