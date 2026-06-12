---
title: "autofs blocking folder creation in /mnt"
date: 2021-09-29
forum: General Help
---

### Post by alain.roger on 2021-09-29
Hi,

To automount shared folders from my NAS, I use autofs.
Till now HDD/partition as NAS shared folders were mounted via /etc/fstab. Now that I use autofs, I can not automount HDD partition via fstab as I can not create a simple folder in /mnt even if I use sudo.
I have 2 HDD partitions I would like to automount at booting time, but once I'm in /mnt the df /mnt display auto.mnt file and no way to create a simple folder using: sudo mkdir Applications command line

How can I do to automount those 2 partitions as gnome disks app, do not automount disks at booting time for unknown reason.

thx.

---

### Post by TheFu on 2021-09-29
According to the *file system hierarchy standards*, /mnt should only be used for temporary mounts for administrative reasons.  Basically, it is a place for admins to put a file system while they copy over other files, before they mount it to the final location.

You can find the standards with any web search ... wikipedia has an article too.

the automounter (which is what autofs uses underneath), needs to have control over the directory where storage is mounted.  It might be possible to use the '-' in the auto.master file to get around this.  I don't know.  I mount my remote dirs under /export/ and /d/ and /misc/.  At work, we mounted user HOME directories under /u/.  I don't recall why, but there was some issue using either /media or /mnt ... I suspect it was a conflict with other Linux processes. I didn't check too hard.

Sorry if this isn't the answer you need.

---

