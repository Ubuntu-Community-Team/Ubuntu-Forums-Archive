---
title: "getting error at boot"
date: 2007-01-25
forum: General Help
---

### Post by presbp on 2007-01-25
I have GRUB and Ubuntu installed on my external harddrive. I partitioned it out so that the first 12 gigs are ubuntu, 270mb are the swap partition, 12 gigs are the FAT32 and the other 250 is unformatted (I wanted Windows to be able to automatically see that..guess not)
I ran the external drive as first in the BIOS and it loaded grub and ubuntu successfully. I checked some stuff got the automount script to mount the fat32 partition then I restarted PC and went into Windows to format the FAT32. In Windows I formatted the FAT32 and I guess since I had the 250gb partition unformatted (using gparted from Ubuntu Live CD) it showed up as unable to do anything but delete. So I plugged in the external and rebooted and ubuntu started loading got about 5-10% done and then i got this error

/bin/sh :can't access tty: job control turned off
[B]
then I shut down unplugged external drive, replugged and booted up.. got the same error except this time after it it said sdb assuming drive write cache write through.
That message concerned me more because in the BIOS my Windows drive is the 2nd drive. 'Would sdb assuming drive cache write through' be doing anything to my Windows drive.. (because I just got Windows re-installed and working again)?[/B]

how do I get this fixed.. arggghhh please help.

---

