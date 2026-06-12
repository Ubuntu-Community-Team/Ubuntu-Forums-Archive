---
title: "dd_rhelp recovering hard disks"
date: 2007-06-05
forum: General Help
---

### Post by adjman on 2007-06-05
If people have not come accross it already, check out this superb link

[http://www.ubuntugeek.com/recover-data-from-a-damaged-hard-disk-using-dd_rhelp.html]("http://www.ubuntugeek.com/recover-data-from-a-damaged-hard-disk-using-dd_rhelp.html")

It is a how-to for recovering data from a faulty hard disk using dd_rhelp which is a script that runs dd_rescue against the drives with some special options. You do need to make sure you have space for the image file it creates, but once you have created the image file and run the fsck -y command against it, it will allow you to mount the drive.

One thing that isn't mentioned is that you need to mount it using loopback, the command is

sudo mount -o loop /dev/hda/image.img /mnt/mountpoint

where image.img is the file created by dd_rhelp and /mnt/mountpoint is the folder you create to mount the image file onto


Saved my entire DVD collection!

---

