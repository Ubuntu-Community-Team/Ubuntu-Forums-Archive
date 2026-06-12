---
title: "unable to activate swap space"
date: 2007-03-31
forum: General Help
---

### Post by dustydawg43 on 2007-03-31
when i type the word free i have 0 swap space how can i fix this problem

---

### Post by taurus on 2007-03-31
Can you post the output of these commands from a terminal?

```
free
sudo fdisk -l
cat /etc/fstab
```

---

### Post by dustydawg43 on 2007-03-31
total           used          free        shared         buffers        cached
    mem:          385880       369072     16808            0            11360         149872
 -/+ buffers/cache:             207840      178040
 swap:                0                   0               0           

    this is what i get when i type    free


when i type sudo fdisk ~l     it says unable to open

---

### Post by Ocxic on 2007-03-31
ignore this, sorry

---

### Post by mlissner on 2007-03-31
I could be sending you down a long and dusty road, but try this:
[http://www.ubuntuforums.org/showthread.php?t=346157&highlight=swap+signature](http://www.ubuntuforums.org/showthread.php?t=346157&highlight=swap+signature)

---

