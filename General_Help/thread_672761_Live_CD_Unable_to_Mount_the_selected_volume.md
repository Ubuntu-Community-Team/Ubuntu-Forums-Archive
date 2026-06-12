---
title: "Live CD Unable to Mount the selected volume"
date: 2008-01-19
forum: General Help
---

### Post by justen503 on 2008-01-19
Hello, 

I am running Ubuntu off of a live CD on my laptop to try and recover some files from Windows since it crashed on me. I am in Ubuntu and it boots up. I go  to the Copmuter where it shows me my HD's and I clikc on my HD in my computer and it tells me "Unable to mount the selected volume." "error: device /dev/hda2 is not removable" "error: could not execute pmount".

I need to get into the HD to back some files to a External USB HD.

I'd appreciate any help I can get.

---

### Post by geraldm on 2008-01-20
Try using a xterm program and then try to mount it.
You might use the filesystem type instead of "auto" in the mount command
```

mkdir /mnt   # needed only if there is no such directory
mkdir /mnt/hda2
mount -t auto /dev/hda2 /mnt/hda2

```

Gerald

---

### Post by justen503 on 2008-01-20
> **geraldm said:**
> Try using a xterm program and then try to mount it.
You might use the filesystem type instead of "auto" in the mount command
```

mkdir /mnt   # needed only if there is no such directory
mkdir /mnt/hda2
mount -t auto /dev/hda2 /mnt/hda2

```

Gerald

That didn't seem to work. It says I didn't have permission. Any other ideas here? Would it help if I installed Ubuntu on a 2nd Partition on the HD?

---

