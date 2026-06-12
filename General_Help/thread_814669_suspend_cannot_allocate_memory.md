---
title: "suspend cannot allocate memory"
date: 2008-05-31
forum: General Help
---

### Post by jrharvey on 2008-05-31
I knew this day would come but i finally got a computer that would not suspend correctly. All my previous ones just worked out of the box. ```
jrharvey@jrharvey-desktop:~$ s2disk
s2disk: Could not lock myself. Reason: Cannot allocate memory
```

anyone had this problem????

---

### Post by pointone on 2008-06-01
Run as root:

```
sudo s2disk
```

---

### Post by jrharvey on 2008-06-01
```
jrharvey@jrharvey-desktop:~$ sudo s2disk

s2disk: Could not stat the snapshot device file. Reason: No such file or directory
```

---

### Post by wenuswilson on 2008-06-01
I get this. I assume you already have uswsusp installed?
> nate@AWESOME:~$ s2disk
The program 's2disk' is currently not installed.  You can install it by typing:
sudo apt-get install uswsusp
bash: s2disk: command not found

---

### Post by jrharvey on 2008-06-01
Ya i have uswsusp installed

---

### Post by pointone on 2008-06-02
Post the contents of your /etc/uswsusp.conf file, if it exists.

Post the output of running "ls /dev/snapshot", please.

---

