---
title: "Can't figure out today's kernel update"
date: 2006-08-03
forum: General Help
---

### Post by MrSmith on 2006-08-03
Today there were quite a few updates. Some having to do with Gnome and CUPS. There was also a kernel image update. I didn't take note of the version and did the install. I did notice no nvidia-glx update was made so I expected X not to work without a manual update. However when I rebooted all worked well. So, I rebooted and went into the grub menu to see the new kernel version. There is only one version listed, it is 2.6.15.26. Which I believe is the one I had in the first place. Could someone explain what happened to the kernel update that was downloaded? It was a the k7 smp/up kernel but I don't remember the version number. However it seems at the end was the number "44" or something like that.

Thanks,
MrSmith

---

### Post by carlosqueso on 2006-08-03
IIRC, you don't get a new GRUB option if there are minor security updates that don't change the version number (like the last one)  It updated, it just won't show up.

---

### Post by MrSmith on 2006-08-03
Thanks. This would make sense as to why there wasn't a need for the nvidia drivers to be updated. After the reboot all was well.

MrSmith

---

