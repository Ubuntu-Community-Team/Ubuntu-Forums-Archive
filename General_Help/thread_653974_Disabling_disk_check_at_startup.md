---
title: "Disabling disk check at startup"
date: 2007-12-30
forum: General Help
---

### Post by tashe on 2007-12-30
How do i make the Ubuntu 7.04 stop making disk error checks everytime it boots?
The boot is  very slow every time i turn it on.
thanks

---

### Post by TidusBlade on 2007-12-30
Im sure it's not supposed to check every single time...
Mine checks every 20 or so boots.

---

### Post by iris-n on 2007-12-30
It really shouldn't.
I wouldn't recommend disabling it, though. Just set it to a lesser frequency with ```
sudo tune2fs -c 42 /dev/hda1
```

change /dev/hda1 to your boot device

and set 42 to the number of boots between checks.

If you really want to disable it, set it to 0.

But I don't think that this would be the issue. Which message do you get when it starts checking?

---

### Post by Princegiri on 2007-12-30
hey i have some problem of this type too.....
pls help me out.... i created a new thread... didnt see this one before creating mine...

[http://ubuntuforums.org/showthread.php?t=654024](http://ubuntuforums.org/showthread.php?t=654024)

---

