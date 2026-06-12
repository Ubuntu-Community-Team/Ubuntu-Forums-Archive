---
title: "XP won't boot HELP!"
date: 2008-06-29
forum: General Help
---

### Post by iae610 on 2008-06-29
Hi, I am having a huge problem and my windows xp wont boot. i get this error "autochk program not found - skipping autocheck". I think my xp is hidden or something. I did ```
sudo fdisk -l

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00ea00e9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8192    65802208+  44  Unknown
/dev/sda2            8193       12161    31880992+   5  Extended
/dev/sda5            8193       11992    30523468+  83  Linux
/dev/sda6           11993       12161     1357461   82  Linux swap / Solaris

```
So I know my partition is there i just cant boot.

Thanks
Ian

---

### Post by VMC on 2008-06-29
Did you try and repair this yourself? In searching around, someone with same issue was using GoBack software, and it lock the Type to '44', like yours. If you did you need to disable that function.

---

### Post by iae610 on 2008-06-29
I do have Norton GoBack and do you have a link to that person with the same problem? Also how would I disable GoBack if i can't boot into xp.

Thanks
Ian

---

### Post by iae610 on 2008-06-30
Never mind, I got the error to go away. I downloaded Gparted and then i open it and clicked the windows drive. After that I unchecked the box that says boot and then ok. That did it for me. Hope this helps someone and thanks a lot VMC

---

