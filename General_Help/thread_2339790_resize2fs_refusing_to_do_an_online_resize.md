---
title: "resize2fs refusing to do an online resize?"
date: 2016-10-12
forum: General Help
---

### Post by jerome1232 on 2016-10-12
I got a new 2tb hard drive, and I moved a my logical volume to it and tried to resize the underlying filesystem, but oddly it's just prints out an error that online resizing is required. I recall it used to just resize online, I see no extra flags in the man page to tell it go ahead and do an online resize.

```
sudo resize2fs /dev/mapper/ubuntu--vg-steamBackup 
resize2fs 1.42.13 (17-May-2015)
Filesystem at /dev/mapper/ubuntu--vg-steamBackup is mounted on /home; on-line resizing required
old_desc_blocks = 19, new_desc_blocks = 64
resize2fs: Permission denied to resize filesystem

```

---

### Post by T.J. on 2016-10-13
> **jerome1232 said:**
> I got a new 2tb hard drive, and I moved a my logical volume to it and tried to resize the underlying filesystem, but oddly it's just prints out an error that online resizing is required. I recall it used to just resize online, I see no extra flags in the man page to tell it go ahead and do an online resize.

```
sudo resize2fs /dev/mapper/ubuntu--vg-steamBackup 
resize2fs 1.42.13 (17-May-2015)
Filesystem at /dev/mapper/ubuntu--vg-steamBackup is mounted on /home; on-line resizing required
old_desc_blocks = 19, new_desc_blocks = 64
resize2fs: Permission denied to resize filesystem

```

In my opinion, you should NEVER attempt to resize an active/mounted filesystem.  You're asking for trouble.

---

### Post by jerome1232 on 2016-10-13
> **T.J. said:**
> In my opinion, you should NEVER attempt to resize an active/mounted filesystem.  You're asking for trouble.

Have you had bad experiences with it personally? I've never had one fail. I've used lvm for a long time and love the fact that I can extend a volume on the fly if I need to.

Fortunately as I was working today it struck me that the reason I migrated to a new disk at all was because the old one was failing, I thought maybe the file system needed an fsck. I booted into recovery mode and fscked it, then booted up normally and the online resize functioned fine.

I wish it had printed a better error message.

---

