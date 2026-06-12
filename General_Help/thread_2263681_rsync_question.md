---
title: "rsync question"
date: 2015-02-02
forum: General Help
---

### Post by jnorris2 on 2015-02-02
I had read (and experienced) that the "normal" rsync options don't work well for exfat, and that I should use something like the following:
 
```
sudo rsync -vrltD --progress --stats
```

I've done that, and it works partially... the problem comes in that it doesn't appear to delete files from the exfat drive. So, if I delete a file from the host and then use the above rsync options, it will copy the new files over, but won't delete the file that was removed from the host. The result is an inaccurate sync.

What am I doing wrong?

---

### Post by ajgreeny on 2015-02-02
Is there some important reason the destination has to be exfat?

---

### Post by jnorris2 on 2015-02-02
It's a drive that's shared between OSX and Ubuntu, so it seemed like the best option....

---

### Post by oldfred on 2015-02-02
If just data, you are ok. But when you restore data you probably have to reset your ownership & permissions as all Windows formats do not support Linux owership & permissions. With data you can use a default setting.

But if backing up any system files, there are not default settins. Every part of system may have different settings. Not everything is owned by root. So you cannot backup system files.

---

### Post by jnorris2 on 2015-02-02
It's just data, but it sounds like maybe I'm better off getting a drive for each system instead of doing it the way I have been....

---

### Post by papibe on 2015-02-02
Hi  jnorris2.
> **jnorris2 said:**
> ...The result is an inaccurate sync.
rsync does not perfectly mirror content by default. To do that you have to use the --delete option. For instance:
```
rsync -av --delete /path/to/content/ /path/to/external/drive
```
For FAT filesystems, it it also good to use the --modify-window options. For example:
```
rsync -av --modify-window=1 /path/to/content/ /path/to/external/drive
```
Some people recommend using a higher number than 1. If 1 does not work well, try 2 or 3, or even 4.

Hope it helps. Let us know how it goes.
Regards.

---

