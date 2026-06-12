---
title: "Check if drive mounted"
date: 2018-08-02
forum: General Help
---

### Post by raleigh3 on 2018-08-02
This does not work even though drive is mounted. ?

```
if grep -qs '/media/andy/KINGSTON_DRIVE/ ' /proc/mounts; then
    echo "It's mounted."
else
    echo "It's not mounted."
fi
```

---

### Post by Holger_Gehrke on 2018-08-02
Take a look in /proc/mounts ... I think you'll find that it lists '/media/andy/KINGSTON_DRIVE' **without** a '/' at the end ...

Holger

---

### Post by raleigh3 on 2018-08-02
Removing / made no difference.

---

### Post by ajgreeny on 2018-08-02
Just to check this a bit more, what does command ```
mount | grep KINGSTON
``` show as output when you know that the disk is mounted?

---

### Post by twily2018 on 2018-08-04
You can use the lsblk command, if the drive is mounted, it will show the mount point.

---

### Post by deadflowr on 2018-08-04
I use conky and conky if statements:
[http://conky.pitstop.free.fr/wiki/index.php5?title=If_statements_%28en%29]("http://conky.pitstop.free.fr/wiki/index.php5?title=If_statements_%28en%29")
[http://conky.sourceforge.net/documentation.html]("http://conky.sourceforge.net/documentation.html")

---

