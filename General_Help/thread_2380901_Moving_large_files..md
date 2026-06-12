---
title: "Moving large files."
date: 2017-12-23
forum: General Help
---

### Post by Poly Hive on 2017-12-23
I have effectively a blank HD of some 1 terra byte capacity. 

I am attempting to move some 250 gig of video files to the video folder and am getting an alert saying there is not enough room.

Can some one explain what I need to do to allocate enough room or what a work around might be please. 

I am running Unbuntu 17.04

Thanks in advance

polyhive

---

### Post by TheFu on 2017-12-23
17.04 support ends in about a month. Probably less than a month, so before moving lots of files, it would be smart to move to 17.10 **or** 16.04 first.  17.10 has an issue with some laptops that might brick the BIOS.

That is a completely separate issue.

Storage management has been the same on all Linuxen the last 25 yrs, so there isn't anything new to be done.
Files are stored in directories.
Directories and files are stored on "file systems".
File systems are created either in a "partition" or a "logical volume."

So - the first things to determine is whether existing file systems have storage for the new files.

**df -h** will show current disk use for mounted file systems. There are other methods, but this works on all Linux/Unix systems desktops and servers.

Assuming the existing, mounted, file systems do NOT have sufficient storage available, the next step is to see if currently connected storage has sufficient empty/unused space to hold a new/extended file system.  The way I'd check is to use **gparted**. This tool will show a graphical view of the physical disks with unused areas marked.  It is also possible to create a new partition, format the file system to something useful, like ext4, using gparted.  However, if LVM is being used, gparted will not tell the truth.

To get the best view of connected storage, I'd use **lsblk**.  Depending on choices made during installation, LVM may or may not be used.  LVM makes storage management extremely flexible, but also adds some complexity. If LVM is being used, post lsblk output and we can move from there.

Regardless, to access a new storage LV or partition, the best method for "mounting" it depends.  If it is permanently connected, like internal storage, then manually editing the /etc/fstab is recommended.  Google finds multiple how-to guides for that.  Mounting through a GUI is **not** recommended, since they use less-good protocols which negatively impact performance.

For temporary connected file systems, using a GUI is probably fine even with the poor performance.  I use autofs for this type of storage myself, but most people would use a GUI.

If the storage involved needs to be physically shared with Windows, then using NTFS as the file system is recommended.  Network sharing with Windows would still use ext4 (or some other Linux-based file system).

If the full storage and the empty storage are next to each other, gparted can often extend a partition, then file system while the partition and file system are in use.  I just expanded a 32G ext4 partition by 8G a few minutes ago.  That partition wasn't using LVM, if it had, thing would have been a little more complicated, but LVM does allow merging storage from different disks into a single file system.  This can be dangerous, but if you understand the risks, it is very common.

Of course, before doing any partition changes, having 100% know-you-can-restore backups is mandatory.  A simple mistake during partition changes can easily destroy all the data on multiple disks.

Hopefully, this is clear. If not, ask a few questions.

---

### Post by HermanAB on 2017-12-23
Wait, there are some things that are not clear.
If you just want to move files from one spot on a file system to another spot on the same file system, then use the mv command and it should be done instantaneously.  Mv only changes the directory entry - it doesn't actually move the data.

If you want to move huge files from a file system on one HD to a different file system on another HD, then I suggest that you use rsync to copy them and once done, delete the originals.  Rsync is a reliable copy command that uses checksums to ensure that the copy is exactly the same as the original.

---

### Post by dragonfly41 on 2017-12-23
I would tweak that suggestion and use the GUI .. grsync.

Also understand first the implications of closing slashes vs. no closing slashes on your SOURCE and DESTINATION paths.

i.e. When and when not to use closing slashes in paths.

Try "dry run" mode in grsync to see what would happen before doing a "real run".

Try copy first rather than moving huge files.  If something happens in mid move you might be in trouble.

---

### Post by mikewhatever on 2017-12-23
"Blank HDD" may be the problem. You need to create a partition and format it. If that's been done, the problem may be with the file system, for example, fat32 has a 4GB file size limit.
It would be a good idea to provide more details, so that we could help without guessing.

---

