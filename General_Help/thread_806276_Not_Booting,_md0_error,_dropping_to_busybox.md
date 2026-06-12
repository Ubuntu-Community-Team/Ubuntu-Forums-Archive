---
title: "Not Booting, md0 error, dropping to busybox"
date: 2008-05-24
forum: General Help
---

### Post by xoddoza on 2008-05-24
I've got a brand new install of ubuntu, latest version. I use it as a fileserver.

PC has 1x 120 gig drive which I use for the OS, and 5x 400 gig drives which are normally arranged in raid 5. 

Last night, it set up the mdadm array, and waited while it rebuilt from the degraded state. Checked it was reporting as clean which it was, before switching off pc and going to bed.

FLicked it on this morning, and wont boot. Initially was jsut dropping to busybox with no reason. Did a search on these forums and found a tip suggesting change the grub boot to remove quiet splash and add all_generic_ide

Runs through all the stuff ok i think, goes through sda -> sdf and then pastes 

md: md0 stopped. about 4 times and thats where it hangs for a while before

Done.
Check root= bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/deisk/by-uuid/ea550cb1-6e59-4605-9730-188a40c196e0 does not exist. Dropping to a shell

Then it boots busybox.

There was no data on the array so all i really want is to be able to boot back into ubuntu so i can finish setting it all up. 

Thoughts?

-xoddoza

---

### Post by fjgaude on 2008-05-24
How do you have the /dev/md0 mounted, in fstab, before you shut down for the night?

---

