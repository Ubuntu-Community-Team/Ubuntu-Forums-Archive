---
title: "ntfs-3g permissions problem"
date: 2007-09-09
forum: General Help
---

### Post by s-lime on 2007-09-09
I followed tutorial to setup ntfs-3g here:
[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

I have a link in Applications > System Tools. I enabled support for external device (the only one option available.)

But when I look at my NTFS disk properties, the owner's permission is set to read. If I try to change it to Read and write, it displays:

The permissions could not be changed.
Sorry, couldn't change the permission of "Projects".

What am I doing wrong?

Thanks for every answer. Really.

---

### Post by merlinus on 2007-09-09
```

gksudo nautilus

```

Navigate to folder (probably in /media), right-click, select Properties, then Permissions.

---

### Post by Endolith on 2007-11-17
> **merlinus said:**
> ```

gksudo nautilus

```

Navigate to folder (probably in /media), right-click, select Properties, then Permissions.

And then what?  What *should* it be set to?

---

### Post by lvleph on 2007-11-24
I am having the same issue. When I used gksudo nautilus, it would not let me change permissions.

---

### Post by lvleph on 2007-11-24
I solved my problem and it might work for you.

```

sudo apt-get install ntfs-config
gksu ntfs-config
sudo unmount /dev/<your partition>
sudo mount -a

```

---

