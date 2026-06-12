---
title: "Trying to recover after harddrive fell out."
date: 2017-01-30
forum: General Help
---

### Post by aquaholic2 on 2017-01-30
Hello! I'm in a little bit of a pickle here, I installed ubuntu fresh on my laptop for the holidays, and I had no external drives to back anything up on. I dropped my laptop, and, surprise, the harddrive was detached. It was an SSD, so there were no moving parts, and it was on carpet, and a one foot drop, so nothing in the laptop itself is damaged, and the drive game out rather gently, the only issue was that it wasn't shut down when it came out. I tried to start it, but the first time was just purple, then saying that there was no bootable images. Anyways, I went to my desktop to see if I could open it up and get my holiday photos off, but all that came up was:

Unable to access 85 GB Volume.
Error mounting /dev/sdb2 at /media/ubuntu/904f8dc0-4f1a-4cfc-b540-3d4ac2a84d13; command line 'mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid," "/dev/sdb2" "/media/ubuntu/904f8dc0-4f1a-4cfc-b540-3d4ac2a84d13"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sdb2,

|missing codepage or helper program, or other error

in some cases useful info is found in syslog - try dmesg | tail or so.



I tried that, and all it came up with was 7-8 or so 'blk_update_request"s - all saying I/O error. Should I post them, and how can I get my files back? I'm relatively new to ubuntu, but I know enough about the command line to update and install things.

thanks!

---

### Post by ajgreeny on 2017-01-30
I assume your desktop machine is also running Ubuntu or at least a Linux OS.

If I'm correct attach the SSD again and then run fsck on the root partition, whatever that shows as in the desktop system.
If the OS on that is Ubuntu the command will be ```
sudo e2fsck /dev/sdx#
``` where /dev/sdx# is probably **/dev/sdb2** according to your error shown, ie, the SSD Ubuntu root partition.

With luck that may flag up and offer a repair to any filesystem problems.

---

