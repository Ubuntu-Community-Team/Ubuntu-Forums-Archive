---
title: "OK to delete dconf and do-release-upgrade in ~/.cache?"
date: 2022-09-06
forum: General Help
---

### Post by klundermann on 2022-09-06
Lately (probably since I upgraded to 22.04) the backup utility gives me an error message to the effect that it cannot backup [FONT=system]~/.cache/dconf[/FONT] or [FONT=system]~/.cache/do-release-upgrade[/FONT] because I do not own them.  Indeed, [FONT=system]ls -ld[/FONT] shows that they and [FONT=system]~/.cache/gstreamer-1.0[/FONT] belong to [FONT=system]root[/FONT]:

```
> [FONT=system]ls -ld dconf do-release-upgrade/ gstreamer-1.0/
drwx------ 2 root root 4096 Aug 22  2018 dconf
drwx------ 3 root root 4096 Oct  2  2020 do-release-upgrade/
drwxr-xr-x 2 root root 4096 Oct  2  2020 gstreamer-1.0/[/FONT]
```

I gather I don't really need to back up .cache in the first place, but I would also like to deal properly with the deeper problem here.  If I'm reading [this thread]("https://ubuntuforums.org/showthread.php?t=2260153&highlight=root+owns+dconf") correctly, I can just delete [FONT=system]dconf[/FONT] and [FONT=system]do-release-upgrade[/FONT].  I would just like to verify: can I safely delete these directories?

And what about [FONT=system]gstreamer-1.0[/FONT]?  I'm not getting any error messages related to it, but it seems wrong that, unlike most files in .cache, it is owned by [FONT=system]root[/FONT] rather than by me.  Should I delete it too, or [FONT=system]chown[/FONT] it?

---

### Post by Impavidus on 2022-09-06
Something in a directory named "cache" can normally be deleted. It may just slow things down a bit when you have to recreate the files later.

There shouldn't be any files owned by root in your home directory. You can chown them or delete them. The gstreamer-1.0 directory is slightly different from the others, as your ordinary user can read that directory, but not write it. So no complaints from the backup routine, as that only has to read the files. I suggest you chown all of them.

This error is caused by inappropriate use of sudo. You ran some applications as root, without informing them that the home directory had changed to /root.

---

### Post by klundermann on 2022-09-06
Thanks very much, Impavidus!

---

