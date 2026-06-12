---
title: "Trying to use External HDD and Windows HDD"
date: 2008-06-01
forum: General Help
---

### Post by Kivamaki on 2008-06-01
I have Windows Vista with a 160GB HDD, I also have 1 external HDD (MyBook 500GB) which is used for storage, and 1 USB External HDD that ubuntu is installed onto. **Ubuntu is not installed on the same partition/hdd as Windows.**

I finally have Ubuntu running smoothly and everything, but I want to be able to access my 500GB External (USB) HDD, and my files on my Windows. But everytime I click the hard drives under "places" it just comes up with "Cannot Mount Volume".

I've searched the forums everywhere but haven't found anything that's helped me. **Here is my "sudo fdisk -l" below.**


> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2ae42ae4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19458   156288000    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbd01e960

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         795     6385806   82  Linux swap / Solaris
/dev/sdb2             796       19457   149902515   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    7  HPFS/NTFS

---

### Post by Kivamaki on 2008-06-01
Bump, help would be appreciated. Thanks!

---

### Post by cybrsaylr on 2008-06-01
I also get that "Cannot Mount Volume" at times using Ubuntu HH, when I try using my ext HHD. It's a windows problem. I have a dual boot system XP/Ubuntu and can use the ext HDD on both XP & hardy but if the ext HDD isn't shutdown properly on Windows it won't work on Hardy till you go back into Windows shut it down by using the 'safely remove hardware' prompt on the lower right taskbar next to the clock in Windows. Once you do that it will mount properly when going back into Ubuntu. 
I used to get that "Cannot Mount Volume" in Gutsy Gibbon also at times.

I believe this holds the same for Vista as well as XP.

---

### Post by cybrsaylr on 2008-06-01
I also get that "Cannot Mount Volume" at times using Ubuntu HH, when I try using my ext HHD. It's a windows problem. I have a dual boot system XP/Ubuntu and can use the ext HDD on both XP & Hardy but if the ext HDD isn't shutdown properly on Windows it won't work on Hardy till you go back into Windows shut it down by using the 'safely remove hardware' prompt on the lower right taskbar next to the clock in Windows. Once you do that it will mount properly when going back into Ubuntu. 
I used to get that "Cannot Mount Volume" in Gutsy Gibbon also at times.

I believe this holds the same for Vista as well as XP.

---

