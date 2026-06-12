---
title: "Nautilus Bookmark to Unmounted Location"
date: 2014-03-15
forum: General Help
---

### Post by Jacob_Gerlach on 2014-03-15
I dual boot Windows 8 and 12.04.

I occasionally want to access files located in my Windows documents folder from Ubuntu.

If I create a bookmark to that documents folder, it disappears when I unmount the windows partition.

Can I make a bookmark in Nautilus that will automatically mount the partition and take me to the location?

---

### Post by tgalati4 on 2014-03-15
Sort of.  You can make a launcher on the desktop that runs a command to manually mount the directory.  Then you can bookmark that launcher.  If you access files daily from your Windows partition, you might consider putting the mount in /etc/fstab so that it is always ready as a local directory mountpoint.  That way, the bookmark will always be ready.

[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by Jacob_Gerlach on 2014-03-15
Thanks.

I don't have time to give this a shot right now, but I understand what I need to do and will set it up when I have a chance.

---

