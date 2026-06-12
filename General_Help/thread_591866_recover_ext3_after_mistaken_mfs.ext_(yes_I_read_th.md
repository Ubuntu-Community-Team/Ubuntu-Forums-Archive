---
title: "recover ext3 after mistaken mfs.ext (yes I read the Wiki sites)"
date: 2007-10-25
forum: General Help
---

### Post by spraygun on 2007-10-25
Hi,

I have mistakenly deleted my hdb1 with mkfs.ext3. Just a second after i hit enter i discovered that mistake and hammered control+c. So mkfs stopped at 367/1407 Inodes.

Yes I have read this site [https://help.ubuntu.com/community/DataRecovery]("https://help.ubuntu.com/community/DataRecovery")
But still it does not help at all. 
testdisk analyses this:
```
Disk /dev/hdb - 200 GB / 186 GiB - CHS 24321 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors
Invalid NTFS boot
 1 P HPFS - NTFS              0   1  1 22958 254 63  368836272
 1 P HPFS - NTFS              0   1  1 22958 254 63  368836272
 2 P Linux                22959   0  1 23086 254 63    2056320
 3 P Linux                23087   0  1 24320 254 63   19824210
No partition is bootable

```

There is no NTFS on it at all and even after a 2 hrs check for MTF it found nothing. 
Finally i've tried a deeper search and it found a linux Partition where above the NTFS was written on. I clicked on recover filesystem but it didnt really work. testdisk says its a ext2 and every other prog dont recognise it at all. 
Please does anyone know another prog or a trick how to recover with these programs? 

I really need to get those files back.

Thanks in advance 
Spraygun

---

