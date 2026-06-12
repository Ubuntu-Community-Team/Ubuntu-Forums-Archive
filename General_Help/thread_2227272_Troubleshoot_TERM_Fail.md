---
title: "Troubleshoot TERM Fail"
date: 2014-05-31
forum: General Help
---

### Post by Kurt_Alan on 2014-05-31
**[SIZE=5][COLOR="#000000"][/COLOR][/SIZE]**

1. Hardware.  Samsung SSD UM410 Series. ATA. BIOS: AHCI not enabled (doesn't exist) because mb is ATA and AHCI is a SATA interface.  This is a 5 year old 8 GB ssd, one of the earliest ones, never been TRIM'd.  When I do: ```
 sudo hdparm -I /dev/sda 
``` I see no mention made of TRIM under capabilities/features.  I do see Mandatory FLUSH_CACHE. Could this be an automated TRIM-like function?

2. Samsung website states that TRIM is supported in all ssd's. 
3. ext4 file system and latest kernal (14.04)
4. After ```
 sudo gedit /etc/fstab 
``` my edit looks like: ```
 UUID=35921f6f-4508-4678-87ae-16bf1c993244 /               ext4 noatime,nodiratime,discard,errors=remount-ro 0       1 
```  Somebody said that the "discard" flag should be "allow-discards" The result of this edit was that I had my first experience using nano--in recovery mode to undo my bad edit so that I could boot to GUI.
5. After I run: ```
 sudo fstrim -v / 
``` I get: ```
 FITRIM ioctl failed: Operation not supported. 
```

Suggestions? Thank you!

---

### Post by Kurt_Alan on 2014-05-31
**[SIZE=5][COLOR="#000000"][/COLOR][/SIZE]**

Dear Moderator:

Would you kindly fix the error in my title?  Please change "TERM" to "TRIM."

I tried to edit via Post Report and Advance Edit (after posting) but I experienced browser fails in both cases.

---

### Post by Kurt_Alan on 2014-06-03
**[SIZE=5][/SIZE]**

Like most Ubuntees, I research my problem before posting.  That would seem to increase the probability that one would not get a response because the answer is not known.

Do you think that is what's happening here?

---

