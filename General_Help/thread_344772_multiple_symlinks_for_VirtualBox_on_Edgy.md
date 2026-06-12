---
title: "multiple symlinks for VirtualBox on Edgy"
date: 2007-01-23
forum: General Help
---

### Post by BillJones on 2007-01-23
When I launched VirtualBox it mounts /dev/hdd as host CD drive. This is not surprising since /dev/cdrom points to /dev/hdd. I can manually change the symlink so that it points to /dev/hdc (my DVD drive) but each time I reboot it is rewritten to /dev/hdd.

How can I force Ubuntu always to point /dev/cdrom to /dev/hdc?

---

### Post by pacificdrums on 2007-01-29
I am having the same problem. Dose anyone have any ideas?:confused:

---

### Post by pacificdrums on 2007-02-05
bump

---

### Post by warjowuch on 2007-04-02
Maybe you should change your title, this way I could not find out what the topic was about...
Sorry, could not be of more help :-) Good luck!

---

### Post by inaneframe on 2007-11-16
```
sudo ln -f /dev/*** /dev/cdrom
```

That *** is whatever device that you want /dev/cdrom to point.

---

