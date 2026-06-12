---
title: "Mounting external drives"
date: 2007-10-19
forum: General Help
---

### Post by Beazel on 2007-10-19
Hi there folks,

    Just a quick noob question about mounting an external USB Hard Disk.  I've just come over from Fedora and used to code as root:

```
/mkdir /media/external
/mount /dev/sdb1 /media/external

```

Doesn't seem to work here though...  It asks for the "type" (it's a FAT32) but I can't figure it.  What's the correct command/syntax?


Also, can I got this Seagate External Thingy to automount?  Like, an icon on the desktop would be all gravy...

---

### Post by angkor on 2007-10-19
> **Beazel said:**
> Hi there folks,

    Just a quick noob question about mounting an external USB Hard Disk.  I've just come over from Fedora and used to code as root:

```
/mkdir /media/external
/mount /dev/sdb1 /media/external

```

Doesn't seem to work here though...  It asks for the "type" (it's a FAT32) but I can't figure it.  What's the correct command/syntax?


Also, can I got this Seagate External Thingy to automount?  Like, an icon on the desktop would be all gravy...


USB disks should be mounted automagically. Have you checked System -> Preferences -> Removable Drives & Media?

Also check if your drive is added in the side pane in nautilus. 

You can also check how your device is connected with the command:

```
dmesg
```

in a terminal and check the last part of the output.

Good luck

---

### Post by Beazel on 2007-10-19
Yeah, it's mount point is /proc but browsing it brings up pages and pages of system type stuff.  Not (seemingly) the contents of the drive.  Any ideas?

Ta

---

### Post by dgray_from_dc on 2007-11-06
Have you tried adding entries to /etc/fstab?  I have found that to be the best solution.  If you don't want to do it by hand, (though I'm mostly a KDE user) I'm quite sure that there is a Gnome equivalent of going in and setting a permanent mount point for /dev/sd(x) that will create the fstab entries for you.

---

### Post by Beazel on 2007-11-06
Can you elaborate on that a little?  I'm running KDE too so should be alright...

At worst I only need to mount this thing once to get all the data across then I can mess about/reformat it/smash it to bits without losing any hard fought work.

This disk (Seagate 250GB USB) has been the most problematic thing I've encountered in my recent Linux days.  It didn't work properly under MS Windows, which it was presumably designed for, and it seems to hate doing anything under ANY linux distribution.  I think it might be time for a new one...

Many thanks
Beazel

---

