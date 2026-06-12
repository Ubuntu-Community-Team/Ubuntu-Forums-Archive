---
title: "can't unmount cdrom"
date: 2007-11-22
forum: General Help
---

### Post by Papas228 on 2007-11-22
ok, well i've checked every where and i've tried a lot of different things but i still can't seem to unmount my cd. i'm using wine trying to install a game and then when it ask for the second disks i can't eject. so if anyone has a solution for me i'd really appreciate it thanks

---

### Post by juan@forum on 2007-11-22
i think your user is not part of the cdrom group

---

### Post by mpierce on 2007-11-22
What version of ubuntu are you using, Feisty, Gutsy or what.

Have you tried to umount the CD-rom. Launch a terminal and do:
  df
This will tell you if the cdrom is mounted. You can then try to umount it with, e.g.,
   sudo umount /media/cdrom

Hope this helps...

---

### Post by Sepehrnoush on 2007-11-24
> **juan@forum said:**
> i think your user is not part of the cdrom group

i have same problem.
my user is default user(when installing ubuntu[gutsy]).
how can i add this user to cdrom group?

---

### Post by Blessed_Coffee on 2008-02-05
It just tells me the device is busy. :(

---

### Post by Shazaam on 2008-02-06
Open another terminal and type in....
```
sudo eject
```

---

### Post by Blessed_Coffee on 2008-02-19
It doesn't work. It just says the device is busy, and that the unmount fails. :/

---

### Post by Blessed_Coffee on 2008-02-19
Okay, try:

```
$ wine eject x: 
```

replace x with the drive you are trying to eject.  cdrom0 should be d:

Hopes this helps :)

---

### Post by frenchn00b on 2008-02-19
> **Papas228 said:**
> ok, well i've checked every where and i've tried a lot of different things but i still can't seem to unmount my cd. i'm using wine trying to install a game and then when it ask for the second disks i can't eject. so if anyone has a solution for me i'd really appreciate it thanks

not adviced : 
```
umount -l /mnt/cdrom
```

l for lazy

---

### Post by loudnlownoma on 2008-02-19
> **Papas228 said:**
> ok, well i've checked every where and i've tried a lot of different things but i still can't seem to unmount my cd. i'm using wine trying to install a game and then when it ask for the second disks i can't eject. so if anyone has a solution for me i'd really appreciate it thanks

How are you starting the install for Wine?  If you are starting from the CD's directory when running "wine install.exe" or whatever the file name is, I have seen people say that can lock the drive and cause trouble when it asks for the next disc.

The preferred way would be:
```
$> wine /path/to/cdrom/install.exe
```

rather than
```
media/cdrom0> wine install.exe
```

---

