---
title: "Cannot mount new HD:  error unknown filesystem type"
date: 2007-12-22
forum: General Help
---

### Post by NoOne2 on 2007-12-22
I'm trying to add a second HD to my Ubuntu install.

The disk was previously used in a RAID setup with a Highpoint controller.

I pulled it out of the RAID array and on a Vista machine repartitioned it to NTFS and used it for a while.

Now I've deleted the partion from Vista and installed it in the Ubuntu box.  I create the partitions, with either Gparted or fdisk, write out the table, format the disk at a type 83.

Everything looks fine but when I try to mount it it comes back saying:

Mount:  unknown file system type :Highpoint RAID member

fdisk says its a Linux type 82...and when I made it a NTFS volume it automounted....now that its a Linux partition it won't mount.

Anyway to change this or do I need something like Seatools and wipe the drive totally clean?

---

### Post by logos34 on 2007-12-22
Use gparted to delete all the partitions.  Repartition and format ext3.  Add f[stab entry(s) and mount points.]("http://www.psychocats.net/ubuntu/mountlinux")

If that doesn't work try Active Kill Disk or Darik's Boot & nuke to wipe it clean. start over

---

### Post by NoOne2 on 2007-12-23
I'll try the wiper.

I used Gparted with no luck, same problem.  It partitions and format but cannot mount.

thanks

---

