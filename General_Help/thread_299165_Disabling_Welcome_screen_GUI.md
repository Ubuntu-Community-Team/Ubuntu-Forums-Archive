---
title: "Disabling Welcome screen GUI"
date: 2006-11-13
forum: General Help
---

### Post by fuzznight on 2006-11-13
Hey, I'm not 100% on if this is the right board but...

I want to disable to welcome screen gui so I can log in using the shell because... using the shell looks cool - I can't seem to find an option to do this in the gdm config file. Any ideas other than ctrl+alt+f1?

---

### Post by yabbadabbadont on 2006-11-13
A quick, but ugly solution would be to remove the execute permission from /etc/init.d/gdm
```
sudo chmod a-x /etc/init.d/gdm
```
You'll probably get some error/warning messages when you boot, but everything should work fine.  To undo the change, just:
```
sudo chmod a+x /etc/init.d/gdm
```

---

### Post by rabid emu on 2006-11-13
Changing the default runlevel in grub.conf ought to do the trick.  I'm PRETTY sure you want to change it from runlevel 5 to 3, but I'm not positive.  I know that's what it was in Fedora but I've only recently moved to Ubuntu and haven't tried it here yet.

---

### Post by yabbadabbadont on 2006-11-13
> **rabid emu said:**
> Changing the default runlevel in grub.conf ought to do the trick.  I'm PRETTY sure you want to change it from runlevel 5 to 3, but I'm not positive.  I know that's what it was in Fedora but I've only recently moved to Ubuntu and haven't tried it here yet.

I don't think that will work with Ubuntu since they seem to start gdm in every runlevel...
```
/home/bubba $ ls -l /etc/rc?.d/S*gdm*
lrwxrwxrwx 1 root root 13 2006-11-12 08:44 /etc/rc2.d/S13gdm -> ../init.d/gdm
lrwxrwxrwx 1 root root 13 2006-11-12 08:44 /etc/rc3.d/S13gdm -> ../init.d/gdm
lrwxrwxrwx 1 root root 13 2006-11-12 08:44 /etc/rc4.d/S13gdm -> ../init.d/gdm
lrwxrwxrwx 1 root root 13 2006-11-12 08:44 /etc/rc5.d/S13gdm -> ../init.d/gdm

```

---

