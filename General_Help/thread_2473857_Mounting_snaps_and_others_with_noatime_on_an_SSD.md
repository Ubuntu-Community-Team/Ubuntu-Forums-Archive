---
title: "Mounting snaps and others with noatime on an SSD"
date: 2022-04-16
forum: General Help
---

### Post by Paddy Landau on 2022-04-16
I have an SSD. To reduce wear (and, I believe, to improve response times), I mount my file systems with [FONT=courier new]noatime[/FONT] instead of the default [FONT=courier new]relatime[/FONT]. That includes [FONT=courier new]/boot[/FONT], [FONT=courier new]/boot/efi[/FONT], and root, which is on LUKS.

I've noticed, however, that all of the other file systems are mounted with [FONT=courier new]relatime[/FONT]. This includes the many snaps. For example:
```
/var/lib/snapd/snaps/vlc_2344.snap on /snap/vlc/2344 type squashfs (ro,nodev,relatime,x-gdu.hide)
```
Wouldn't it be better for me to remount them as [FONT=courier new]noatime[/FONT]? For example:
```
mount --options=remount,noatime /snap/vlc/2344
```
Or, maybe there's a way to change the default for snaps, so that they load as [FONT=courier new]noatime[/FONT] in the first place?

There are also pseudo file systems such as cgroup, FUSE, and so forth, but I suspect that they are all RAM file systems and therefore unimportant to change; please correct me if I'm wrong.

What is your opinion — should I bother with this? Or am I fussing about something trivial?

---

### Post by vanadium on 2022-04-16
Unless I am wrong, these file systems are mounted read only anyway, so writing will not occur even with the relatime option. So you should not worry with respect to "wear" of the ssd. Whether the system does not attempt to write access times at all, or just fails because the system is ro, is another question. If the system does attempt to write, it would be better to have a noatime option, else it does not matter in any way (although still it may not make any noticeable difference for practical purposes).

---

### Post by Paddy Landau on 2022-04-16
> **vanadium said:**
> Unless I am wrong, these file systems are mounted read only anyway…
You are right!

I missed that.

Thank you for pointing what should have been the obvious &#128563;

---

