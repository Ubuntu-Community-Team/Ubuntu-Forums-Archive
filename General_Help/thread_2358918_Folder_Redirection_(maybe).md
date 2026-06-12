---
title: "Folder Redirection (maybe?)"
date: 2017-04-18
forum: General Help
---

### Post by Sean_Ooley on 2017-04-18
I think I described the basic topic of this situation. Here's the scenario: I have multiple hard drives. One of them has multiple folders, Videos, Documents, Pictures, etc. I would like to have the Videos, etc. folder in my Home folder open up the folders on this drive. I don't think I can do this with fstab, but I'm sure linux and the fine people here has a solution. Thank you.

---

### Post by Dennis N on 2017-04-18
Two Video folders, one in home and the other on a separate data partition (can be on another drive), can be bind mounted. All contents of the Video folder on the data partition appear in the Video folder in home. With a bind mount, the special Video folder icon in home still appears the same. No link icon appears, since this is not a symbolic link.

I do the following to automate this on startup. In /etc/fstab these two entries are needed in this order. The first mounts the data partition, the second bind mounts the folders.

```
UUID=xxxxx /mnt/Common-Files ext4 defaults 0 2
/mnt/Common-Files/Videos /home/dmn/Videos none bind 0 0

```

---

### Post by TheFu on 2017-04-18
Look up **symbolic linking**.
Be very careful using bind mounts.

---

### Post by Dennis N on 2017-04-18
Yes indeed. A little reading and practice would be in order for either method. Another thing with bind mount - any contents of the Video folder in home become invisible and inaccessible until you unmount the other folder, so best to have it empty.

---

### Post by Sean_Ooley on 2017-04-21
Thank you, I'll get to that soon. Got a million things to do =(.

---

