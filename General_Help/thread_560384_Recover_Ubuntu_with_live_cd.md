---
title: "Recover Ubuntu with live cd?"
date: 2007-09-26
forum: General Help
---

### Post by wangjiaji on 2007-09-26
:(Hi everybody,

All of a sudden, my Ubuntu 7.04 refuses to boot up, what I got is this
> Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
and the recovery mode doesn't work ether, and it says that something is trying to access the hardware directly.

I have the live cd but I really don't like to reinstall the whole thing, can I recover it with the live cd:confused:

Thanks!

---

### Post by pay on 2007-09-26
You can chroot into your old environment to try and fix it```
sudo su
mkdir /mnt/ubuntu mount /dev/hda3 /mnt/ubuntu
mount -t proc none /mnt/ubuntu/proc
mount -o bind /dev /mnt/ubuntu/dev
chroot /mnt/ubuntu /bin/bash
export PS1="(chroot) $PS1"

```

---

### Post by wangjiaji on 2007-09-27
YES! Thank you, it works!

I fixed it with a `[COLOR="Blue"]dpkg --configure -a[/COLOR]'

BTW, while mounting the disk, the `exec' option should be turned on.

---

