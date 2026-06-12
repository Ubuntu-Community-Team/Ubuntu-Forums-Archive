---
title: "mdadm raid5, 'Unable to access location'"
date: 2019-04-02
forum: General Help
---

### Post by pandaman92 on 2019-04-02
Hi I'm having trouble with my 16Tb (5x4tb) mdadm array. It works fine untill i get a power cut or turn off the machine forcefully, and then upon restart and i try to access it i get the error message "Unable to access location - Error mounting system-managed device /dev/md0: can't read superblock on /dev/md0"

What's most frustrating is got it to work again a good 6 months ago but i'm and idiot and didn't write down what i did. So i know its possible and i shouldn't have to loose any data, and i remember it being rather simple but i cant remember what i did.

I ran mdadm --detail and this is what i got


[HTML]/dev/md0:        Version : 1.2
  Creation Time : Wed Jun  6 17:31:25 2018
     Raid Level : raid5
     Array Size : 15627548672 (14903.59 GiB 16002.61 GB)
  Used Dev Size : 3906887168 (3725.90 GiB 4000.65 GB)
   Raid Devices : 5
  Total Devices : 5
    Persistence : Superblock is persistent

  Intent Bitmap : Internal

    Update Time : Tue Apr  2 16:06:18 2019
          State : clean 
 Active Devices : 5
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : NAS:0  (local to host NAS)
           UUID : ba6b1fc2:13f583af:fa9b2c4b:007a08fb
         Events : 5257

    Number   Major   Minor   RaidDevice State
       0       8       16        0      active sync   /dev/sdb
       1       8       32        1      active sync   /dev/sdc
       2       8       48        2      active sync   /dev/sdd
       3       8       64        3      active sync   /dev/sde        5       8       80        4      active sync   /dev/sdf[/HTML]

So all the disks seem to be ok and i remember it being 1 or 2 simple commands, are there any other things you need to know to help me? please let me know and thanks in advance!

---

### Post by SeijiSensei on 2019-04-02
Buy a UPS so you won't have these problems again.  Any large storage server like this one needs to be protected from power cuts.  And never turn off the system from the power switch except as a last resort.

It looks like mdadm successfully constructed the device from its components.  Try running

```
sudo fsck /dev/md0
```

which will check the actual filesystem (ext4 I assume) that you created on top of the array.

---

### Post by MagnusL on 2019-04-03
Hi!

I'm also having troubles with a raid5-volume, separate thread here: [https://ubuntuforums.org/showthread.php?t=2415836](https://ubuntuforums.org/showthread.php?t=2415836). Is it correctly understood that you do not need to reassemble the array, it is just mounting that is the trouble? FOr my part, there is no raid volume on boot at all (but the data is there, once re-assembled. 

Maybe your mount-options in fstab is wrong?

Magnus

---

