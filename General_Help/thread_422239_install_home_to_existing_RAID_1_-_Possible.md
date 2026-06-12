---
title: "install /home to existing RAID 1 - Possible?"
date: 2007-04-25
forum: General Help
---

### Post by hotani on 2007-04-25
I have an existing RAID 1 (250GB). It is software RAID. I want to install Feisty onto a separate 80GB drive, and use this array for /home.

If possible, it would be nice to just "point and shoot." That is, run the installer, point to the RAID 1 array for /home, the 80 for /, and be done. 

But the installer does not see the array. The alternate install CD threatens to destroy data to manipulate or work with RAID--perhaps I am being overly cautious here, but I really don't want those drives nuked.

Tell me there is a simple, GUI-based method of doing this that I have overlooked. How can I install to RAID if the installer does not recognize it? Is there a way to do this with the alternate CD in which my existing data is untouched?

---

### Post by hotani on 2007-04-25
I'm thinking of setting this up in a way that takes RAID out of the installation equation. Having the array set up as /home would be nice (would a symlink be asking for trouble?), but I can easily devote a partition of the 80GB drive to /home and point to my stuff on the array. Then upgrades (via clean install) will be much less painful, and I'll still have a somewhat solid backup plan if a drive fails.

Ideas?

---

### Post by asipi on 2007-04-26
tip:
try install on the 80 GB partition only (separate a swap would be nice though :) ) then mount your raid device to /mnt, copy everything from the actual /home to /mnt then edit your fstab to mount your raid device to /home (from next boot), then you umount /mnt and delete your existing files in /home and mount the raid device to /home or reboot either...

---

### Post by hotani on 2007-04-26
Thanks, I like that method better than what I ended up doing. I used the alternate CD which saw my RAID 1 (had to go into 'configure RAID' then just click 'finish' for the array to show up in the drive list), and allowed me to point to it for /home. 

Although this worked, I ended up [unable to boot](http://ubuntuforums.org/showthread.php?t=423500) from the 80 because the installer put grub on the wrong drive (and incorrectly at that.). I am able to boot via "boot from first hard drive" on the cd options, but that's it. Still working on getting a functional grub going.

---

