---
title: "[SOLVED] Cant unmount a volume."
date: 2008-07-06
forum: General Help
---

### Post by Kain000 on 2008-07-06
Hey everyone,
so it's 3 am in Colorado right now and I've finely worked out the kinks setting up the  NFS clients and server side, *hopefully*  and I had the shared folder on the server mounted to my desktop as public docs, and at first it worked, however after a while of messing around with the export conf file in the NFS setup to get it to export to both my computers Ip's, it stopped pointing to a file on my server. For some reason when I try to execute it, the "volume" acts as if I had requested a new open office doc, because that's what it does, starts open office and asks what sort of doc I want to create.  Cant explain it, but solved by creating another public docs volume to mount witch does work... (so far).  so I don't expect anyone to know what's causing that but if someone by chance does know i'd be interested to find out.

Really I just want to unmount the original volume form my desktop, but I cannot because " it is not in the fstab and I am not root" Im not sure how to become root to unmount this volume, or if that will even resolve what ever the fstab problem is.
any help would be awesome!

thanks everyone.
-sean

---

### Post by bubba_169 on 2008-07-06
Try this in a terminal:

```
sudo umount 'destination' 'mountTo'
```
replacing 'destination' with the full path to the block device (e.g. /dev/sda1) and 'mountTo' with the folder you mounted the volume to (e.g. /media/sda1)

---

