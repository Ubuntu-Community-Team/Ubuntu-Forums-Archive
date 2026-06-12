---
title: "Configuring automounted USB drives"
date: 2007-03-07
forum: General Help
---

### Post by Iskendar on 2007-03-07
Hi all,

 I've got this external harddisk which I keep more or less permanently plugged in. Problem is it gets automounted by the first user to log in, and permissions are assigned to that user only. I'd like to configure it so that rw permissions are granted to the entire users group, but I don't know where to configure this for the automount feature. Is that a part of kde by the way, or is it separate?

---

### Post by joselin on 2007-03-07
You have to put it in your /etc/fstab and mount it.
```
man fstab
```
```
man mount
```

---

### Post by Cadoo on 2007-03-07
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)
2/3 down the page

---

