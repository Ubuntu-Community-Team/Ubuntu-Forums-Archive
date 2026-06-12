---
title: "cryptsetup resize returns device not active despite cryptdisk status returning active"
date: 2019-09-29
forum: General Help
---

### Post by f1ndingwalden on 2019-09-29
[I](originally posted [here]("https://unix.stackexchange.com/questions/544288/cryptsetup-resize-returns-device-not-active-despite-cryptdisk-status-returning"))

[B]the solution is to re-open the device and changing the byte size to a number divisible by the offset (in this case 4096):
[/B]
                  [/I]after runing cryptsetup status, take note of the offset. Change the byte size to the next lowest number divisible by that number. In my case the number was 4096 bytes or 8 512-byte-sectors. The steps I took to solve the issue were:
1. close the device (if open)
```

# vgchange -an 
# cryptsetup luksClose cryptdisk

```
2. reopen it and restart the process with the modified byte size;
```

# cryptsetup luksOpen /dev/device cryptdisk
# vgchange -ay 
# cryptsetup -b 377520128 resize cryptdisk 

```

[I][B] -------original post-------
[/B][/I]
I am in the process of resizing LVM-on-LUKS, referring to [these]("https://wiki.archlinux.org/index.php/Resizing_LVM-on-LUKS") [two]("https://ubuntuforums.org/showthread.php?t=726724") posts as guides. I had done this once before smoothly, but I have run into a strange problem. When I run 
 ```
#cryptsetup -b 377523479 resize cryptdisk

```
Returns first:
```

device-mapper: resume ioctl on cryptdisk  failed: Invalid argument

```
and then:
```

Device /dev/mapper/cryptdisk is not active.

```

However, 
  ```

#cryptsetup status cryptdisk 
 /dev/mapper/cryptdisk is active and is in use.
  type:    LUKS1
  cipher:  aes-xts-plain64
  keysize: 512 bits
  key location: dm-crypt
  device:  /dev/nvme0n1p3
  sector size:  512
  offset:  4096 sectors
  size:    438766176 sectors
  mode:    read/write

```

Running 
```
# vgchange -ay
```
beforehand does not change output.

Additional info:
```
# dmsetup table
cryptdisk: 0 438766176 crypt aes-xts-plain64 00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000 0 259:3 4096
ubuntu--vg-swap_1: 0 16572416 linear 253:0 360040448
ubuntu--vg-root: 0 360038400 linear 253:0 2048
```

```
 # pvdisplay   
--- Physical volume ---   PV  Name               /dev/mapper/cryptdisk   VG Name                ubuntu-vg   PV Size               <180.00 GiB / not usable 3.00 MiB    Allocatable           NO   PE Size               4.00 MiB   Total PE               46079   Free PE               106   Allocated PE           45973   PV UUID               O8SubL-AdqH-sKU1-Jrir-KJ9c-kHk1-Dc8ODl
```

```
# lvdisplay   
--- Logical volume ---   LV  Path                /dev/ubuntu-vg/root   LV Name                root    VG Name                ubuntu-vg   LV UUID                 UuHOj4-Hxvu-SQDZ-5Bu4-Qrp8-pPfe-bC3XRi   LV Write Access         read/write   LV Creation host, time ubuntu, 2017-09-06 01:48:35 +0000    LV Status              available   # open                 0   LV Size                 <171.68 GiB   Current LE             43950   Segments                1   Allocation             inherit   Read ahead sectors      auto   - currently set to     256   Block device          253:1
--- Logical volume ---   LV Path                 /dev/ubuntu-vg/swap_1   LV Name                swap_1   VG Name                 ubuntu-vg   LV UUID                 41lkRI-wOri-ocGc-5GOt-Ld97-fhDd-aG7rgz   LV Write Access         read/write   LV Creation host, time ubuntu, 2019-09-29 07:59:57 +0000    LV Status              available   # open                 0   LV Size                 7.90 GiB   Current LE             2023   Segments                1   Allocation             inherit   Read ahead sectors     auto   -  currently set to     256   Block device           253:2
```




Any suggestions appreciated, I don't know how to proceed and am rather stuck. Also in a time crunch (who isn't :( ).

---

