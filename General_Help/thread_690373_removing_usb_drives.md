---
title: "removing usb drives"
date: 2008-02-07
forum: General Help
---

### Post by caen1944 on 2008-02-07
I have encountered a strange problem and am wondering if anyone has any imput.

I put in a small fileserver for the office based on ubuntu 7.04 about 6 months ago. It used 2 1TB usb drives to store data. One drive gets copied over to the other by rsync every night. I have a third usb drive that I swap out once a week for the backup drive. I used udev rules to assign these otherwise identical drives different device names (which is very cool and useful)

Here is my issue. When I swap the drives weekly, I unmount the backup drive and simply turn it off. Then I plug in the other drive, turn in on, wait a few seconds, and mount it. 

However, very occasionally (it has happened twice), I unmounted and turned off the backup drive when the main drive appeared to be be doing something (the red activity light was on). At the exact second that I turned off the backup drive the main drive activity light to stayed on solid and essentially crashed the drive. I had to restart the system, and use fsck to recover the journal on the main drive. 

Am I removing usb hard drives correctly (umount and then just turn off)? Has anyone seen this behavior before? Is it a known usb hardware issue or potentially a bug in the linux kernel or usb module? How can I let others know of this problem if it is a general issue?

Any help would be appreciated. 

Thanks.

---

### Post by macogw on 2008-02-07
When you unmount, it has to sync the drive.  There could be stuff in the buffer, waiting to be written to the drive.  If you type "sudo sync" first, that'll write the buffers, then you should be able to unmount/turnoff-immediately.  As it is, it's probably trying to sync during unmount and that can take a few seconds (or with a TB drive....a minute or two), so you're probably yanking before it's actually done unmounting fully.

---

### Post by caen1944 on 2008-02-07
Thanks for the advice. I had forgotten about that sync command. I'll always do that from now on. 

Also, I talked to an electrical engineer in the office. He said that USB systems are notoriously tricky for electrical problems. Apparently poorly built devices can send a spike on the ground plane of the powered bus, and interfere with the operation of other devices. He said it is even more likely that a power spike from the cheapo power supply on the usb disk can occur when I turn off that disk, and knocked out the other disk. I had both disks plugged into the same power strip, which he recommended I don't do.

Anyway, I'll us sync and I'll get a second power strip, and hopefully it won't happen again.

Thanks

---

