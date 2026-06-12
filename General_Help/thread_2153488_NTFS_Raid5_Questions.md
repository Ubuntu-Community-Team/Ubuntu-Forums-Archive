---
title: "NTFS Raid5 Questions"
date: 2013-06-11
forum: General Help
---

### Post by Maniacal on 2013-06-11
I've had a multi-boot (Ubuntu/Win7) system for several years. Installed an ESATA 4 disk raid5 array over a year ago. Chose to format whole array in ntfs so that either OS could use it. Prior to Ubuntu 13.04 my only concern about drive performance was I couldn't move anything on array to Trash. It had to be deleted. Now with a fresh install of Ubuntu 13.04 64 bit there are two concerns: Still can't move anything to Trash, it has to be deleted. The other being a delay on bootup of Ubuntu, I get a purple screen saying drive is not there or not ready and gives me choice to wait, skip mount, or manual recovery. I've just been waiting and 15 to 30 seconds later Ubuntu will see drive and finish boot. Array is in my fstab file with entry "UUID=7ADCDD3DDCDCF3FB    /media/Buffalo    ntfs    rw    0    0". This is the same entry I've always used yet it behaves differently in Ubuntu 13.04. Is there a problem with fstab entry or could it be that required kernel module isn't loading early enough? Any and all help will be greatly appreciated.

---

