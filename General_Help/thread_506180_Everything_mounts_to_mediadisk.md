---
title: "Everything mounts to /media/disk"
date: 2007-07-21
forum: General Help
---

### Post by pickarooney on 2007-07-21
Is there any way of forcing my digital camera, mp3player and usb memory stick to mount to specified places. As it is, the first one I plug in mounts to /media/disk and the next to /media/disk1, which plays havoc with my scripts for copying photos and music to the hard drive.

---

### Post by brent113 on 2007-07-22
Just a guess: is there anything listed in your /etc/fstab that looks familiar?  If so, try changing that to what you want.  If not, sorry, I'm out of ideas.

---

### Post by vanadium on 2007-07-22
Go to places - computer. When you right-click a drive, you have a Volume tab. Click on "settings" and there, you can specify your custom mount point, aka, just type the label under which you want the device mounted in the future in the "Mount point" field (warning: just put one label, i.e. no path name and no label with spaces!). You will first need to unmount. Next time, it should be mounted with the name you specified.

Alternatively, label your disks. By default, Linux uses the volume label name if available. See [http://www.debuntu.org/device-partition-labeling](http://www.debuntu.org/device-partition-labeling)

---

### Post by pickarooney on 2007-07-22
Second option should work, but is a bit long-winded. As I'm using Kubuntu I'm not sure how to bring up an equivalent of the Volume tab which I presume is in Nautilus?

Just thinking - I actually have two separate SD cards, both of which I want to mount under /media/camera (obviously only one at a time). Wonder will that be an issue?

---

### Post by PointSource on 2007-07-22
I have had a little bit of trouble somewhat along the same lines, and here is a condensed version of my solution (ie. please read between the lines):
 - look under /dev/disks/by-uuid/ for your card/partition/whatever (pull out, put in a few times)
 - edit /etc/fstab to mount that device node to wherever
 - add "users" to options so it is mountable by all
 - mount it

Each UUID is different, so its a fairly surefire way of identifying each filesystem.
This way is probably not the "right way", and its fairly hackish, but it works.

---

