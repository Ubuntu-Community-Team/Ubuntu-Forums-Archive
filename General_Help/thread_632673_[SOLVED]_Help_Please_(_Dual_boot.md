---
title: "[SOLVED] Help Please :( Dual boot"
date: 2007-12-05
forum: General Help
---

### Post by CodyGuitarist on 2007-12-05
Ok so I had dual boot working and something  messed up on my windows side so I reinstalled the windows file(Overwrote the existing file; not a new install).

Now it doesnt pick up ubuntu. I know its still on there because my c:\ only shows up use 106GB when its a 200GB hd   so the partition still exists.

Any idea of how I can fix this?  Can I fix this?

---

### Post by rsambuca on 2007-12-05
You can just use any linux liveCD and reinstall the grub bootloader to the mbr.

---

### Post by CodyGuitarist on 2007-12-05
:D thanks

---

### Post by IeU on 2007-12-08
> **rsambuca said:**
> You can just use any linux liveCD and reinstall the grub bootloader to the mbr.
oh, ive done that so many times to no sucess for me.


sda - 160gb linux
sdb - 150gb windows xp
sdc - 500gb data hd
sdd - 320gb data usb hd
sdf - 1gb usb stick

installed that way, at the end on the installation the checkbox to install grub was checked.

restart and i boot directly to windows xp.

so i downloaded a window app that could might help me access the linux hd, acronis os selector.

i get then at booting prompted if i want to boot the windows hd or linux hd,

i select linux hd, it boots and then i get prompted with grub, asking me if i either want to boot linux or xp, lol.

wasnt it written to the mbr ? i would like to install grub on mbr, and get rid of this grub on the start of the sda

how should i do that ?

---

### Post by IeU on 2007-12-08
bump

---

### Post by rsambuca on 2007-12-08
Post your /boot/grub/device.map and also check the boot order of the drives in your bios.

---

### Post by IeU on 2007-12-08
> **rsambuca said:**
> Post your /boot/grub/device.map and also check the boot order of the drives in your bios.

i will, but i think i cannot choose in my bios which hd should act as main, i think i can just choose the order of, hd > cd > lan > other > floopy

for now,
```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x38ef38ee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         243     1951866   82  Linux swap / Solaris
/dev/sda2   *         244        1459     9767520   83  Linux
/dev/sda3            1460       19457   144568935   83  Linux

Disk /dev/sdb: 150.0 GB, 150039945216 bytes
240 heads, 63 sectors/track, 19381 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xcbed35df

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19380   146512768+   7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x909e622d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       60802   488384512    7  HPFS/NTFS

Disk /dev/sdd: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ffc810

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       38912   312560608+   7  HPFS/NTFS

Disk /dev/sde: 1014 MB, 1014497280 bytes
65 heads, 32 sectors/track, 952 cylinders
Units = cylinders of 2080 * 512 = 1064960 bytes
Disk identifier: 0x32b73a58

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1         953      990704    b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(967, 64, 32) logical=(952, 39, 32)
ubuntu@ubuntu:~$ 
```


i dont know how to explain exactly what i think is happening is,

at the end os the installation, Grub is being installed on "hd0", that would be at the mbr of "/dev/sda" or ?

but when i boot my pc, the first/main drive seem by my bios ( i do not know if i can change which drive should be seen as first/main ) is the /dev/sdb.
how do i tell the installation to write grub on the mbr of sdb ?

---

### Post by IeU on 2007-12-08
another question,

i create on my 160gb hd,
2gb for swap
10gb for /
150 for /home

is that ok, what would be the use to create another partition with /boot ?
is it useful ? if yes, how big should it be ?

---

### Post by rsambuca on 2007-12-08
1.  I do not see the need for a separate /boot.
2.  Please post the output of:  cat /boot/grub/device.map
3.  You can definitely change the boot order of the drives in the bios.  You just have to find the proper place.  That is your biggest problem, and easiest fix.

---

### Post by IeU on 2007-12-09
> **rsambuca said:**
> 1.  I do not see the need for a separate /boot.
2.  Please post the output of:  cat /boot/grub/device.map
3.  You can definitely change the boot order of the drives in the bios.  You just have to find the proper place.  That is your biggest problem, and easiest fix.


thanks mate, changing that hd order thing solved my problem :)

im now trying to figure out how to install my X-FI ExtremeGamer sound card . . .

ubuntu identifies it as an usb-sound-card ? wtf ? lol ^.^

---

### Post by IeU on 2007-12-09
> **rsambuca said:**
> 1.  I do not see the need for a separate /boot.
2.  Please post the output of:  cat /boot/grub/device.map
3.  You can definitely change the boot order of the drives in the bios.  You just have to find the proper place.  That is your biggest problem, and easiest fix.

oh, one more thing  . . .
```

felipe@felipe-desktop:~$ cat /boot/grub/device.map
(hd0)   /dev/sda
(hd1)   /dev/sdb
(hd2)   /dev/sdc
(hd3)   /dev/sdd
(hd4)   /dev/sde
felipe@felipe-desktop:~$
```

---

