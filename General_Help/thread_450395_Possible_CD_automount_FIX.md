---
title: "Possible CD automount FIX"
date: 2007-05-21
forum: General Help
---

### Post by jholsenback on 2007-05-21
Hello,

I may have stumbled upon a fix for auto mounting audio CD's. Here's what I did:

I added piix to /etc/initramfs-tools/modules the did:  sudo update-initramfs -u and rebooted.

My /etc/fstab entry looks like this:
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

I noticed that it made these device files:
brw-rw---- 1 root disk   3,  0 2007-05-21 07:05 /dev/hda
brw-rw---- 1 root disk   3,  1 2007-05-21 10:06 /dev/hda1
brw-rw---- 1 root disk   3,  2 2007-05-21 07:05 /dev/hda2
brw-rw---- 1 root disk   3,  5 2007-05-21 07:05 /dev/hda5
brw-rw---- 1 root disk   3, 64 2007-05-21 07:05 /dev/hdb
brw-rw---- 1 root disk   3, 65 2007-05-21 07:05 /dev/hdb1
brw-rw---- 1 root disk   3, 66 2007-05-21 07:05 /dev/hdb2
brw-rw---- 1 root cdrom 22,  0 2007-05-21 07:05 /dev/hdc

It auto mounted the audio CD and brought up the proper application to play the CD

This all came from a user jerrylamos thread that I used to get around the "can't access tty" error that stopped me from running the 7.04 LiveCD ..... I recalled that there was a mention of doing something after the system was installed ..... so I figured what the heck. If someone could offer why this worked that might be helpful. I guess I'm saying do this at your own risk!

Cheers Jim

---

