---
title: "Can't access my extra external drives"
date: 2014-04-20
forum: General Help
---

### Post by troysos on 2014-04-20
I  just built a new htpc and I'm moving my external drive full of data (4 drives, 13TB in all) to the internal of my new computer. I pulled the casing off of one and plug every thing in my new computer but ubuntu won't see it. When I open "disk" it will show the model number and can see the drive but I can't open it. They are fomated ntfs. 


I'm running an i5, asrock extreme 6 mother board, boot drive is Samsung evo ssd. Ubuntu 14.04.

Edit: I've been looking around but I guess I mean Ubuntu doesn't mount the drives.


Thanks!

---

### Post by coldcritter64 on 2014-04-20
Open a nautilus window, your home folder will do, make sure you have the sidebar showing (pressing F9 on your keyboard will toggle it on/off). 
You should be able to see the ntfs partitions in the sidebar. 
Clicking on them will mount them and open the partition in the window, it will stay mounted till you log out or unmount it manually by pressing the "eject button" in the sidebar. 

You can add entries to /etc/fstab to automatically mount the partitions at startup, if you are putting them into the computer on a more permanent basis. Research various /etc/fstab "mount options" for your ntfs partitions to have them mounted to suit your needs at startup.

Check  [[COLOR=#0000ff]--this link--[/COLOR]]("https://help.ubuntu.com/community/Fstab") to learn about /etc/fstab.

---

### Post by troysos on 2014-04-20
It doesn't show up in the side bar of nautilus. That's what I was hoping it would do. I'll check out your link. Thank you.

---

### Post by troysos on 2014-04-20
I don't' know if it makes a differences but I just hooked the same drive up through a usb port and it mounts automatically.

---

### Post by coldcritter64 on 2014-04-20
> **troysos said:**
> I don't' know if it makes a differences but I just hooked the same drive up through a usb port and it mounts automatically.

Yes, /etc/mtab would be mounting them automatically as removable devices. /etc/fstab is used to mount partitions from fixed drives/devices automatically at startup.

With the drives hooked up internally you could try using the code next in a terminal, to get the required UUID etc for an fstab entry.

```
sudo blkid -c /dev/null
```this code will poll your devices, gives you the device number, device label, UUID and filesystem type for all your connected partitions including any mounted removable devices.

It is best to do mounting of internal drive partitions by UUID, if you later move or reconnect the cabling differently device numbering can change for partitions, whereas by using UUIDs your system can still be found easily. That command will give you the UUIDs to use in /etc/fstab.

Example output of the above code from an ntfs (storage only) partition on a docked 500GB laptop HDD.
> ```
/dev/sdj7: LABEL="ntfs-h500g" UUID="4470F866231E57FE" TYPE="ntfs" 

```

You will need to create mount points for your partitions in /media eg /media/[LABEL], where [LABEL] is the partition label you have used. Permissions for accessing the ntfs partitions are set in /etc/fstab when mounted automatically to these mount points.

```
sudo mkdir /media/[LABEL]
``` for each partition being mounted automatically.

Once you check out fully the docs (previous link) and maybe research mount options for ntfs as per your needs and set some fstab entries, another code to check an entry in fstab (before requiring it at boot time) is,
```
sudo mount -a
```
using this in terminal will show any errors in the mounting of the partitions BEFORE you need them for booting.

I am a bit surprised nautilus didn't pick the partitions up when connected internally ... :-k

---

### Post by troysos on 2014-04-22
I was away from the computer for a few days but I ended up just reformatting the drive to ext4. It wouldn't show all 3tb (only 2tb would show) but I searched around and I had to change the partition table. I have a new problem but I'm going to start a new thread. Thank you!

---

