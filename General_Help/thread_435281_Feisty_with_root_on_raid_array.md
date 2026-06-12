---
title: "Feisty with root on raid array"
date: 2007-05-06
forum: General Help
---

### Post by ryanc on 2007-05-06
I have an existing feisty install on /dev/hda2 that I would like to convert into a raid1 array with hdc2. So far I have been able to create /dev/md1 which consists of my new hdc2 partition, copy all data from hda2 to the new md1 device, reboot with /dev/md1 mounted as root. 

Next I added the original root partition (hda2) to the md array and waited for /proc/mdstat to show that md1 was fully synced and it contained two disks (hda2 and hdc2). 

At this point I thought I would be all done however when I boot specifying my root as /dev/md1 I get a repeating message to my screen (just after all the hd's are detected):

md: array md1 already has disks!

This continues over and over and does not appear to stop. At this point I am not sure how to continue. One thing to note is that both partitions are type linux and not "raid auto detect" because I was having trouble with raid autodetect trying to use hda2 as a raid partition before I had added it to md1. 

I added break=mount to my kernel options in grub with no effect (so it appears this error condition is occurring while assembling md1 and not at mount time.

Also my mdadm.conf contains a definition of md1 that contains hdc2. My theory was that init was assembling md1 but then getting to mdadm.conf and trying to assemble it again even though it already contained both disks. So I booted from a live cd and mounted the drives individually commenting out the arrays from mdadm.conf... this did not have any effect on the boot however I suspect it is because the initramfs version of mdadm.conf still has the arrays defined?

Please help! I am currently downloading the alternate cd so that I can use mdadm after booting from the cd (the live cd doesn't appear to have mdadm).

Thanks!

---

### Post by ryanc on 2007-05-07
I found a solution to my issue. 

Once I booted from the alternate cd and was able to mount /dev/md1 I chrooted to that environment and deleted mdadm.conf, ran update-initramfs, and rebooted. The next boot worked as expected.

It appears that mdadm did not like auto assembling the raid array and having it specified in the configuration file? 

Hope this helps someone.

---

