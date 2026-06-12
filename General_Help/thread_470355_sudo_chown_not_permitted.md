---
title: "sudo chown not permitted"
date: 2007-06-10
forum: General Help
---

### Post by notatoad on 2007-06-10
i have an external fat32 hard drive mounted at /mnt/ext with my movies and tv on it.  when i try  execute ```
sudo chown -R kyle /mnt/ext
``` i get a whole bunch of errors saying that the operation is not permitted.

here is the fstab line that mounts it```
/dev/sdb1	/mnt/ext	vfat	rw,user,auto	0	0
```

chmod also doesn't work.  it doesn't give any errors, it just runs with no result.  how can i make myself the owner of my external drive, or at least give myself write permissions?

---

### Post by taurus on 2007-06-10
What if you edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and replace this line

```
/dev/sdb1	/mnt/ext	vfat	rw,user,auto	0	0
```
with this.

```
/dev/sdb1	   /mnt/ext	vfat	iocharset=utf8,umask=000   0	0
```
Save it and reboot.  Now, you should be able to write to /mnt/ext.

---

