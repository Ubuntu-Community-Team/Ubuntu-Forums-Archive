---
title: "NTFS -&gt; ext3, partition not showing in places menu"
date: 2007-01-18
forum: General Help
---

### Post by dexter on 2007-01-18
I've been using linux for a while not and got frustrated that i cannot modify anything on my music partition since it is a ntfs partition. 

So i decided to change it into an ext3 partition. I created a backup of my files, unmounted the volume, used gparted to reformat the partition using ext3 and rebooted (it told me it would be wise to reboot). After rebooting the partition did not show up under the places menu. Turns out it still wasn't mounted. I modified my fstab line to 
```

/dev/sda1      /media/music    ext3  defaults   0   1

```
To get the partition /dev/sda1 mounted on  /media/music. After that i couldn't read/write to it, turns out the permissions were set to root only. I changed permissions of /media/music to
- File owner: root
- File group: plugdev
My other partition have the same properties. Now i can read/write to it.

The problems i'm no facing are
- I can see the lost+found dir, which should only be visible to root.
- The partition isn't showing up onder the places menu which i find very annoying. When i go to computer and check the properties of the partition it says 'unknown' for File owner and File group, the other partitions are set to root and plugdev respectively. I tried changing that using gksudo nautilus, going with root to computer but i cannot see the disk at all as root in the computer window. How do i get met partition back now in the places menu ?

---

### Post by dexter on 2007-01-18
Hmz, the problem seems to have solved itselve after a reboot. I can't remember changing anything that would cause it to work all of a sudden. Strange...

---

