---
title: "How to change automount permissions?"
date: 2020-04-30
forum: General Help
---

### Post by ldcdc on 2020-04-30
Hello,

I apologize in advance if I don't use the correct terminology here. 

My situation is this: in Kubuntu, when I delete a file (move to trash) from an automounted partition (say an external HDD), instead of being moved to a /hdd/.Trash or /hdd/Trash-$userid folder, which takes an instant, it is being copied  to ~./local/share/Trash, and in the case of a long video clip, could take minutes. This is unlike Ubuntu, or any other sane approach, and it wastes writes on my SSD.

There is a 10 years old bug filed over at KDE about this: [https://bugs.kde.org/show_bug.cgi?id=76380](https://bugs.kde.org/show_bug.cgi?id=76380)

By the time another 10 years pass, I need a workaround.

What can I do to set permissions/paramenters uid=1000,gid=1000,umask=077 when automounting drives? I read something about udev and udisks2, but can't find a true step by step guide.

Thank you!

---

### Post by wildmanne39 on 2020-04-30
*Thread moved to **General Help for a more appropriate fit**.*

---

### Post by TheFu on 2020-05-01
I don't know of any GUI method to accomplish it.  The first issue is that the external disk isn't using an native Linux file system. That would fix  the mount issues and permissions. If the disk doesn't need to be physically connected to Windows, then that is my first, best recommendation. Convert to ext4 file system. That is a destructive conversion, so make a backup first.

If you are stuck with NTFS, then you can use one of the 2 automouter tools.  These are either autofs or systemd-automount.  For directly connected USB storage, my attempts to get the systemd-automount working have all failed. It does work extremely well for network storage like NFS, however.  This makes me think the issue is with me and my understanding, not a failing of systemd.  BTW, I'm not a fan of systemd in general, so that last statement wasn't easy to type.

Autofs is a little more involved. There is an ubuntu how-to guide, but as with most of those guides, it is very complete when you really just need 2 lines in 2 files, after installing autofs - for your specific, NTFS, mount needs.

[https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs) is the ubuntu guide.  My web search terms were: "ubuntu autofs"  Knowing autofs is nearly impossible, if you don't know it already. ;(
Steps:
[LIST=1]
[*]install autofs
[*]add/modify one line in /etc/auto.master
```
/-      /etc/auto.misc   --timeout=60 --ghost
```
[*]add/modify one line in auto.misc or whatever the name of the other file you choose
```
/mnt/250G  -nodev,windows_names,nosuid,noatime,async,big_writes,timeout=2,fstype=ntfs,uid=1000,gid=1000,fmask=0002,dmask=0002    LABEL=250G
```
must be on a single line.
[*]sudo service autofs restart
[/LIST]

Then it will be mounted under /mnt/250G ... and access will be as fast as NTFS allows.  It will only be mounted when accessed. A few minutes after all the files are closed on the storage, the mount will be removed.

I don't mount storage under /mnt or /media, but most people probably should so that snap packages may, someday, have access.

The LABEL=  part is the label for the partition. The label must be unique to the system/storage.  I prefer to use that method to mount USB storage.  UUID= or a path to a device will work fine too.

I see you want a umask of 0077. That should work, just remove my fmask and dmask entries. No spaces are allowed in the mount options.

As for trash, there are many different implementations. Since I don't use any GUI, I don't use trash stuff.  For me, that's why there are daily, automatic, backups.  If I accidentally delete something important, yesterday's backup set has it. So does the set from last week, last month, 3 months ago, so it isn't really gone until 90 or 120 days later when old backups are finally removed by the backup tool.

---

### Post by ldcdc on 2020-05-01
TheFu, thank you for taking the time to reply in such detail.

> The first issue is that the external disk isn't using an native Linux file system. That would fix the mount issues and permissions. If the disk doesn't need to be physically connected to Windows, then that is my first, best recommendation. Convert to ext4 file system. 

Funny you should write that. As a test, I had already created 4 partitions on an USB drive: FAT32, NTFS, ext4 and exfat. The NTFS partition was the only one that mounted automatically in my Kubuntu 20.04; the others require a click in the file manager to mount. Surprise: the ext4 partition ended up being mounted as read only. So... even if I wanted to switch, ext4 would be an even worse choice in my situation. Trash still not working in any of them (didn't bother with remounting ext4 rw though). 

The "problem" with the autofs suggestion is that it still means I have to manually enter settings for every single USB stick or external HDD I enter in the machine. That I've already done for a couple of them via /etc/fstab. I was hoping for a general way of automounting with custom options.

I tried using an udev rule as detailed here: [https://wiki.archlinux.org/index.php/Udev#Mounting_drives_in_rules](https://wiki.archlinux.org/index.php/Udev#Mounting_drives_in_rules). That didn't work as advertised; probably because it ultimately relies on systemd. :P

> Since I don't use any GUI

Now that's something I've never even contemplated doing. :D

---

