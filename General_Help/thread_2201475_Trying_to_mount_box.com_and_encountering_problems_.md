---
title: "Trying to mount box.com and encountering problems with fuse."
date: 2014-01-24
forum: General Help
---

### Post by Dr3x1 on 2014-01-24
I've searched for quite some time and all the information I've found that looked helpful seems to be outdated. Every package I've seen mentioned is either already installed or no longer exists. After setting up davfs2 and configuring it with all the data needed for my box.com account I go to mount it and I get the following:

```
# mount box
/sbin/mount.davfs: can't open fuse device
/sbin/mount.davfs: trying coda kernel file system
libkmod: ERROR ../libkmod/libkmod.c:505 kmod_lookup_alias_from_builtin_file: could not open builtin file '/lib/modules/2.6.32-042stab076.8/modules.builtin.bin'
FATAL: Module fuse not found.
/sbin/mount.davfs: no free coda device to mount
libkmod: ERROR ../libkmod/libkmod.c:505 kmod_lookup_alias_from_builtin_file: could not open builtin file '/lib/modules/2.6.32-042stab076.8/modules.builtin.bin'
FATAL: Module coda not found.

```

I get a login notification from box.com so I know it got it that far, but that's it.

Edit: If it helps: This is a VPS running Ubuntu 13.10 64bit.

---

### Post by Habitual on 2014-01-24
```
sudo modprobe fuse
``` and try again?

---

### Post by Dr3x1 on 2014-01-24
Tried that. :(

# sudo modprobe fuse
libkmod: ERROR ../libkmod/libkmod.c:505 kmod_lookup_alias_from_builtin_file: could not open builtin file '/lib/modules/2.6.32-042stab076.8/modules.builtin.bin'
FATAL: Module fuse not found.

---

### Post by Habitual on 2014-01-24
Bummer. Maybe contact the VPS support folks and ask?
Was is "pre-built" (like an OpenVZ node) or I guess I'm asking how the OS got installed there.

---

### Post by Dr3x1 on 2014-01-24
I just used the Ubuntu image provided by their control panel. I was having slightly different, but similar issues with CentOS. I'll try contacting them. It's unmanaged so I'm not sure how much they are willing to assist, but if it's a problem with their image then maybe they can help... :-/

---

