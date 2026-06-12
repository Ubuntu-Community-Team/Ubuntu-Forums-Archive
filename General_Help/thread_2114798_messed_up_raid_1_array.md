---
title: "messed up raid 1 array"
date: 2013-02-11
forum: General Help
---

### Post by courghan on 2013-02-11
Hello All, i need some help as i am quite new to linux/ubuntu.

I had Openmediavault running on my Prolian microserver with 1 OS drive, 2 x5oogb hd and 2 x 2tb hd in a raid 1 array (md127 created with mdadm a good while ago).

I had the idea of installing ubuntu desktop 12.10 on a differetn OS drive, replacing the one with openmediavaults. The OS drive is the 5th drive in my system. I made the mistake of installing ubuntu without disconnectin the other 4 drives so I think it installed grup on a raid drive as this is the first drive in the system. Of course it didn't boot so I reinstalled disconnecting the other drives and it ubnuntu now starts correctly.

Problem was the raid array: there was no trace of /dev/md127 and both its drives were flagged as boot. I flagged them as raid with gpart and using mdadm -scan I managed to get the /dev/md127 array visible and mountable again (the 2 drives do not show up on their own but now i have only one "Raid Array").

The problem is that it still has problems as the drives are missing the superblock, wrong magic number, etc. I would really like to fix it as I don't think it is reliable now. 

The drives (sda and adb) have 1 XFs partition and about 8 gb of free space, which i also cannot format (sdb is reported busy even if unmounted) or use for extending the data partition. I think there were swap partitions there which somehow got deleted.

I really need to get this fixed without loosing data...I don't even have a spare 2tb dirve for backing up everything and rebuild the array from scratch.

What data/logs do you need to look at?

thanks!!

---

### Post by SaturnusDJ on 2013-02-11
You don't have a back-up...but clearly you should have one because your data barely survived.

You might be able to do a (re)create with mdadm using the exact same settings as when the array was created first, but if you don't know all the info you could lose access to your data.

Buy a drive and back-up before trying to fix this.

---

### Post by courghan on 2013-02-11
Thanks for the advice. The data has survived, I can access it now, even mediatomb has no problem in accessing it...it is just the raid conf that is dodgy.

---

