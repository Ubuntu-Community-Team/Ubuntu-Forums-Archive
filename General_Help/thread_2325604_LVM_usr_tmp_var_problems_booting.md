---
title: "LVM /usr /tmp /var problems booting"
date: 2016-05-23
forum: General Help
---

### Post by bojam on 2016-05-23
I have been running Ubuntu 12.10 for sometime no problem.... except I was running out of space on the hdd and thought if I reorganised the disk with LVM I could make better use of the space I have.

  I originally had the partitions for: / /usr /usr/local /opt /tmp /var /home swap and a windows partition.

  The / partition is on a ssd and the others on the hdd.

  I started by combining the /usr and /usr/local this went ok.   Then created a lvm2 partition in which I created /opt /isos and /vms as LVs all in one LG.

  I rebooted the laptop ... all was ok the system recognised the new LVs... So I thought lets go and try the /usr /tmp /var and swap.   

  This is when the system wouldn't reboot properly ... so tried mounting the LVs as /newtmp /newvar /newusr and it booted so tried mounting them individually but the laptop would not boot if any of the LV /usr /var or /tmp  were used.

  I then thought it maybe the boot process was not starting LVM, I couldn't find any evidence of it in the logs except when none of the problem LVs were selected.

  I tried making the initrd but the results were the same... so I did an install of 12-10 using lvm2 and it worked with all but /boot in a LV!

  I thought I read somewhere that LVM was compiled into the kernel now?  The 16.10 initrd has lvm but the 12.04 doesn't.

  Ok so how do I get my system as I want it ie with all except the / and the windows partition in LVM?

---

