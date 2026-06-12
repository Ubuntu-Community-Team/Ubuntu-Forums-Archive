---
title: "Can't See AutoFS Mount Folders Until Called Explicitly"
date: 2017-06-23
forum: General Help
---

### Post by rebeltaz on 2017-06-23
I installed Ubuntu 16.04 (with gnome-session-flashback) on a system yesterday and I installed autofs to mount some network shares. I then created the mountpoints under /mnt - multimedia; shop.docs; and shop.data - and rebooted. Same thing I've done on other systems on the past. When I rebooted, I navigated to /mnt - both with ls and in the file browser - there was nothing there, even with hidden files enabled. I tried to re-mkdir the directories, but I couldn't. If I explicitly call the directory, though - with either [ls /mnt/multimedia] or by typing the directory into the file browser - the directory is displayed and it now shows up under /mnt. 

There is nothing different between this and another system on which I installed this and I didn't have this problem on that one. Any reason why this is behaving this way and how I can fix it?

---

### Post by TheFu on 2017-06-23
Why? It is a security and resource feature.

You want the "ghost" option for automounter.
```
$ egrep ghost  /etc/auto.*
/etc/auto.master:/Data /etc/auto.Data --timeout=60 --ghost

```

No need to reboot. Just restart **autofs** after any config changes.

BTW, /mnt/ is for temporary mounts. I wouldn't use it for mounts that I'd setup via the automounter. Similarly, I avoid using anything under /media/ since that is where the OS automatically mounts stuff. Best to avoid issues proactively, right?

---

### Post by rebeltaz on 2017-06-23
Cool. Thank you. 

I've always mounted to /mnt. Is there any reason not to, specifically? I appreciate the help!

---

### Post by TheFu on 2017-06-23
Standards.

File system hierarchy standards say not to, except for temporary storage.  That means processes that need a temporary mount can assume /mnt/ is available and might take it. That effectively hides anything mounted below.

Feel free to look up the standard. It is easily found.

---

