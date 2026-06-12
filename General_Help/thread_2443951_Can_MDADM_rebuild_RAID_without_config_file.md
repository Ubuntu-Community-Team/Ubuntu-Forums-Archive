---
title: "Can MDADM rebuild RAID without config file?"
date: 2020-05-22
forum: General Help
---

### Post by Steve_Daubs on 2020-05-22
I have a home media server that is running Ubuntu 14 something that has 7 drives in it: a single SSD boot drive and 6 HDD drives in a RAID6 format setup using MDADM. The SSD is just the bootable OS, the MDADM configuration, and the media server software with the data on the 6 HDD drives.

We recently lost power and found that the BIOS is not seeing the SSD drive while it is finding the other 6 drives properly. As there is no bootable drive to find, the server doesn't start. As it turns out, this is a known issue with SSD drives that lose power suddenly like in a power outage. I've been trying the various techniques to have the BIOS find the SSD drive again, but so far, they haven't worked.

My question for this forum is, if I have to replace the SSD drive, can MDADM find the RAID6 configuration from the 6 HDDs? And if so, what commands do I run?

---

### Post by lvm on 2020-05-22
Yes, it can. Install mdadm package and run 'mdadm --assemble --scan'. If everything is ok run 'mdadm --detail --scan >> /etc/mdadm/mdadm.conf' and edit the last ARRAY line in mdadm.conf you've just added to give it a permanent name e.g. /dev/md1 - by default it starts numbering md devices from 127 down and that may change. Add a line to /etc/fstab to mount it automatically. Reboot to test.

---

### Post by Steve_Daubs on 2020-05-23
Thank you for the quick reply. I'm still trying to boot off the original SSD drive which still isn't recovering while I wait for a new SSD drive to be sent. It will likely take a few days to make it here. I'll update this thread once I have it running again.

---

