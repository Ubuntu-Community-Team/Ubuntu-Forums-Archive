---
title: "Replacing a disk with computer on"
date: 2023-02-07
forum: General Help
---

### Post by michael351 on 2023-02-07
I have Ubuntu 22.04 installed and two external 4TB data drives (ext4) connected via USB. I wanted to shutdown one drive and replace it with a different 2TB drive without
shutting down the computer. The drive is sync'd and unmounted. Is there an easy way to just unplug one drive and plug in the next one and have lblk see it as the new drive?
When I swapped out the drives, lsblk still showed the prior drive listed.

---

### Post by TheFu on 2023-02-07
Use  'dmesg -w' to see when the USB swap is seen.  USB devices are supposed to be hot-pluggable, thought mount control/needs depend on how you mount each file system.  

I don't allow Gnome / any DE to mount storage.  So I have to explicitly mount then umount file systems.  

With different LABELs on the file systems, setting up 'autofs' will make this fairly automated, just need to wait for the 1 min between swaps and ensure all files are closed on the storage so autofs recognizes it as unused and remotes the mount.  Then you can pull the USB out, wait 10 seconds, insert the other drive, wait 10 seconds (or so, depending on what 'dmesg -w' shows, then access the storage in the expected location.  BTW, mount using the LABEL, so you have full control over mount options.

I use autofs for all network and USB storage.  Anything that isn't permanently connected like SCSI or SATA or eSATA or infiniband connectors would be.

---

