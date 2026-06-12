---
title: "Failed to activate swap /swapfile after fiddling with Disks"
date: 2022-05-01
forum: General Help
---

### Post by -_- on 2022-05-01
I was trying to backup my data to an external USB SSD.

I connected the SSD and noticed it wasn't auto-mounting.

So I went into Disks and fiddled a bit with the settings. I turned on Mount disk on startup for this external SSD, and gave it some mount point, /mnt/backup, nothing special.

There are now two cases, depending on whether the external SSD is connected or not.

When the external SSD is connected, it's treated as the root file system, and the internal SSD I usually use isn't mounted.
When the external SSD isn't connected, I am seeing:

```
systemd[1]: Failed to activate swap /swapfile.
[FAILED]: Failed to activate swap /swapfile.
[DEPEND]: Dependency failed for swap.
```

I am then taken to the Ubuntu terminal.

I'm using Xubuntu 21.10.

My ultimate goal is to:

- Be able to boot into Xfce again, keeping all of my data intact. (Creating another external backup right now, just to be sure...)
- Be able to auto-mount the external USB SSD, so that I can easily backup my data onto it next time. The internal SSD should always have the root file system.
- Understand what happened, so as to avoid doing it next time, if possible :)

[Here]("https://paste.ubuntu.com/p/2vNKKh2Bcn/") is a boot-repair extract.

---

### Post by TheFu on 2022-05-02
Don't mount using a GUI.
Use the /etc/fstab or autofs.

The file system matters. Non-native file systems like NTFS or FAT32 or exFAT shouldn't be used, especially for backups, unless the backup tool specifically supports those.  Most do not, but duplicity, DejaDup, Duplicati all do.  I think all the others will either fail or drop extremely important information required for a proper backup.

If the / file system isn't there, then the swapfile that ubuntu started placing into /swapfile.img around 20.04 won't work.

I'm unwilling to look at any pastebin which mandates a login, so I can't see the boot-info. Sorry.

---

