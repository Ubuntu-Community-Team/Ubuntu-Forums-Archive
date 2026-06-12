---
title: "Linux Newbie. Oracle10g Install"
date: 2007-02-22
forum: General Help
---

### Post by s0ckpuppet on 2007-02-22
Ok here goes.

I have installed Ubuntu server in a VMware session. I have successfully installed it as it was easier than SUSE or Redhat.
I have enabled root as I needed to use root in the gnome desktop (Im doing /ect/init.d/gdm start / stop) to get into the desktop as it won't let root in by default

The two problems I am having is cpio is not working. I have downloaded Oracle 10g and gunziped then cpio -idmv ship.db.lnx32.cpio which worked fine on both SUSE and Redhat but on Ubuntu it sits there doing nothing? Any ideas?

The second is using a CD.  I copied the oracle install folder from Redhat to a windows share then burn't a CD, the CD mounts and I can see the contents when doing ls /cdrom or ls /media/cdrom0 or ls /media/cdrom  but when I try to run the installer I get the error: Bash: /cdrom/runInstaller: /bin/sh: bad interpreter permission denied

Help

---

### Post by nodesert on 2007-08-24
did you try it as supervisor

like sudo ./nameOfinstaller

---

