---
title: "How do I make multiple disks appear as one?"
date: 2007-11-17
forum: General Help
---

### Post by bungnati on 2007-11-17
Is there a way to make multiple disks look like one drive? I have 2) 250GB hd's and want the computer and applications to see only one larger 500GB disk. Is this possible? Any help would be great. Im using 6.06 64bit server edition.
Thanks

---

### Post by nick_h on 2007-11-18
In Windows you can have multiple drives ( C:, D:, etc...) but in Linux there is only one "drive"  ( / ).  Physical disks have to be mounted within the one directory structure.

I don't think I understand your question fully - perhaps you could explain further.

---

### Post by bungnati on 2007-11-18
I want to make a computer as a NAS and have multiple drives mapped from windows to look as one. 2) 250GB to look like 1) 500Gb and have windows see a mapped 500GB drive.

---

### Post by rob3r on 2007-11-18
Get a RAID card? Anything less than a RAID card on board is going to significantly hurt performance.

I'm sure there is a software way to do this, but I'm not the guy to ask about that.

---

### Post by shae on 2007-11-18
You should look into using LVM.

---

### Post by bungnati on 2007-11-18
Isnt the "device Mapper" included in the linux kernel an LVM?

---

### Post by bungnati on 2007-11-18
Also Performance is not an issue as i will be having slow speeds over wireless as it is.

---

### Post by Rev60073 on 2007-11-18
RAID-5 (striping and mirroring) can concatenate several physical drives into a single logical volume.

---

### Post by bungnati on 2007-11-18
Ive installed the LVM from this page "http://ubuntuforums.org/showthread.php?t=216117" and cant get it to start even using the "gksu system-config-lvm" any ideas,.,.
Ive got it to work now but i have to destroy partition info and redo it "All Data Will Be Lost" when initializing the drive. Not a very appealing option to me at this point. 

Raid 5 requires min 3 drives, correct. capacity is (Size of Smallest Drive) * (Number of Drives - 1) so if I have 3) 250GB drives capacity is 500GB. Let me know if im wrong.

 What would I need to have Ubuntu do raid 5 by software?

---

