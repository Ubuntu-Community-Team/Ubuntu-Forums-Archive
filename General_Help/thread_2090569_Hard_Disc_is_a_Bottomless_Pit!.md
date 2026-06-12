---
title: "Hard Disc is a Bottomless Pit!"
date: 2012-12-02
forum: General Help
---

### Post by ceil210 on 2012-12-02
I used to have plenty of space on my Ubuntu partition.  Now I have diddly squat.

```
agardner@ubuntu:~$ df -h /
Filesystem      Size  Used Avail Use% Mounted on
/dev/loop0       26G   18G  7.9G  70% /
```

Where the heck is Ubuntu storing all of these bytes!?

---

### Post by jerome1232 on 2012-12-02
Will list your toplevel directories and their sizes
```
sudo du -hx --max-depth=1 / 2>/dev/null
```

Will find files 5 Gigabytes and bigger
```
sudo find / -size +5G
```

---

### Post by ceil210 on 2012-12-02
Thank you so much :)

---

