---
title: "Empty /etc/fstab - how to recover basic system LVM mountpoints? (/, /tmp)"
date: 2021-11-17
forum: General Help
---

### Post by jeffrice47 on 2021-11-17
I am currently running Ubuntu 20.04.3 LTS.  Due to a glitch, my /etc/fstab got zeroed out.  Unfortunately, my backups didn't cover the /etc directory as I thought they were (a good lesson for testing your backups, but I digress...)

My system is headless but it boots and I can get in via ssh.  Initially it mounts everything as ro, and lots of commands fail because I have no space on /tmp.  (you can see the main drive says 100% full, which was not the case prior to the /etc/fstab borking.)

How do I figure out what the original commands in my /etc/fstab were for the base system?  (ie, / and /tmp)  I can rebuild the rest of the /etc/fstab from there.  I can't believe I did this.  Or that my backups were incompetently configured. :oops:

df -h:
```
Filesystem                         Size  Used Avail Use% Mounted on
udev                               7.8G     0  7.8G   0% /dev
tmpfs                              1.6G   42M  1.6G   3% /run
/dev/mapper/ubuntu--vg-ubuntu--lv  229G  229G     0 100% /
tmpfs                              7.8G     0  7.8G   0% /dev/shm
tmpfs                              5.0M  4.0K  5.0M   1% /run/lock
tmpfs                              7.8G     0  7.8G   0% /sys/fs/cgroup
/dev/loop0                          11M   11M     0 100% /snap/canonical-livepatch/114
/dev/loop1                          56M   56M     0 100% /snap/core18/2246
/dev/loop3                         100M  100M     0 100% /snap/core/11993
/dev/loop2                          62M   62M     0 100% /snap/core20/1169
/dev/loop4                          81M   81M     0 100% /snap/ffmpeg/1286
/dev/loop5                          74M   74M     0 100% /snap/lxd/21858

```

lsblk:
```
NAME                      MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
loop0                       7:0    0  10.1M  1 loop /snap/canonical-livepatch/114
loop1                       7:1    0  55.5M  1 loop /snap/core18/2246
loop2                       7:2    0  61.9M  1 loop /snap/core20/1169
loop3                       7:3    0  99.4M  1 loop /snap/core/11993
loop4                       7:4    0  80.1M  1 loop /snap/ffmpeg/1286
loop5                       7:5    0  73.1M  1 loop /snap/lxd/21858
sda                         8:0    0 232.9G  0 disk 
&#9500;&#9472;sda1                      8:1    0     1M  0 part 
&#9500;&#9472;sda2                      8:2    0     1G  0 part 
&#9492;&#9472;sda3                      8:3    0 231.9G  0 part 
  &#9492;&#9472;ubuntu--vg-ubuntu--lv 253:0    0 231.9G  0 lvm  /
sdb                         8:16   0   3.7T  0 disk 
&#9492;&#9472;sdb1                      8:17   0   3.7T  0 part 

``` 


blkid:
```
/dev/sda2: UUID="ef290e8c-98a6-425d-805f-7a80d032b819" TYPE="ext4" PTTYPE="dos" PARTUUID="ba9694e0-ccb3-48bc-adce-e4af742fbabb"
/dev/sda3: UUID="21OqZm-EJGv-DsXV-2A4Z-VO0s-aUIt-oJ9DFy" TYPE="LVM2_member" PARTUUID="762a4781-f8c5-4878-8c3d-a48f123412b1"
/dev/mapper/ubuntu--vg-ubuntu--lv: UUID="a244020d-3135-49bc-a53f-ea9651c37a8e" TYPE="ext4"
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/sda1: PARTUUID="ea9c9455-cd30-4f08-9058-c2427d7d903c"
```

Ignore /dev/sdb - it's a data drive and should not be necessary for operations.
/dev/sda2 looks like my /boot partition.  (it contains grub, initrd.img, vmlinuz, etc)
/dev/sda1 i'm not sure about - mount says `wrong fs type, bad option, bad superblock on /dev/sda1, missing codepage or helper program, or other error.`

lvdisplay:
```
  --- Logical volume ---
  LV Path                /dev/ubuntu-vg/ubuntu-lv
  LV Name                ubuntu-lv
  VG Name                ubuntu-vg
  LV UUID                oKq7h1-fIJl-CFHb-NUMp-Qfmn-ElGT-M2tnCY
  LV Write Access        read/write
  LV Creation host, time ubuntu-server, 2020-01-04 15:58:49 -0500
  LV Status              available
  # open                 1
  LV Size                <231.88 GiB
  Current LE             59361
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:0
```

vgdisplay:
```
  --- Volume group ---
  VG Name               ubuntu-vg
  System ID             
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  3
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                1
  Open LV               1
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               <231.88 GiB
  PE Size               4.00 MiB
  Total PE              59361
  Alloc PE / Size       59361 / <231.88 GiB
  Free  PE / Size       0 / 0   
  VG UUID               OQi5bR-ToNe-yCEN-raEF-Cfuw-S81W-VILFtC
```

---

### Post by Tadaen_Sylvermane on 2021-11-17
It's odd that you can get ssh access without an fstab. My thinking is you need to mount the root and swap, and nothing else.

```
[COLOR=#000000][FONT=&amp]/dev/ubuntu-vg/ubuntu-lv / ext4 defaults,errors=remount-ro 0 1[/FONT][/COLOR]
```

[COLOR=#000000][FONT=&amp]You will need to mount that /dev/sda2 into /boot as well. I'm unsure of that line because I don't typically keep a separate /boot partition unless I'm doing EFI. Make sure to use the UUID, not the /dev/sda2 part.

Swap is optional. Once it boots and you have full access then you can find the name of the swap file and mount it in the fstab after the root volume.

```
/.swapfile none swap sw 0 0
```

Something is clearly amiss though because root doesn't just fill up like that. Possibly run away logs. Another thing is while testing a backup of some sort the path was wrong and it sent the backup to the root instead of it's target thereby filling it up. You best bet would be attach a screen and boot a live distro. Chroot in and figure out whats going on.

/dev/sda1 is likely the bios boot partition / efi partition. Again it depends on what you did. If it's the the efi partition then it will need to be mounted at /boot/efi. If bios boot then I don't think you need to do anything with it other than let it exist.[/FONT][/COLOR]

---

### Post by jeffrice47 on 2021-11-17
Yeah, had a runaway issue on root.  Took a bit to work that one out.

Yes, thanks for the tip on swap - I was forgetting it was a file not a partition nowadays.

---

