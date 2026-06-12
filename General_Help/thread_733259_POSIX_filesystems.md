---
title: "POSIX filesystems"
date: 2008-03-23
forum: General Help
---

### Post by fela on 2008-03-23
Just to let anyone know, the way POSIX* mounts drives isn't like windows. In POSIX, all drives mount somewhere under / (the root directory), and there is always one drive mounted at / (the startup drive). Where in windows you would: ```
cd D:\
``` (if i'm right, i've never used windoze as a daily OS so understandably rusty on DOS), in POSIX you DO NOT have drive letters as mount points, so the equivalent would be: ```
cd /media/drive_name
``` assuming your drive is called drive_name and it's mounted at /media/ (in POSIX, you can mount a drive anywhere you want, literally, but the most common points are /mnt and /media)

*POSIX: *nix OSes ([http://en.wikipedia.org/wiki/*nix]("http://en.wikipedia.org/wiki/*nix") for more info)

---

