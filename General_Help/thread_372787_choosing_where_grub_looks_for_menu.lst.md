---
title: "choosing where grub looks for menu.lst"
date: 2007-02-28
forum: General Help
---

### Post by EugeneK on 2007-02-28
I created a new partition, installed OpenSUSE (in addition to my pre-existing Ubuntu installation) and now grub uses the menu.lst in the OpenSUSE /boot directory. 

Since all of the menu.lst changes made during an apt-get upgrade in Ubuntu are made to the one in the Ubuntu /boot directory, I have to manually edit the OpenSUSE one to reflect these changes. 

How do you change the directory that grub goes to to find a menu.lst at boot time?

---

### Post by john.nicholls on 2007-03-01
Try [www.linuxjournal.com/article/4622](www.linuxjournal.com/article/4622)

---

### Post by rsambuca on 2007-03-01
If you enter```
sudo grub
```

Then at the grub> prompt, enter```
find /boot/grub/stage1
```

Grub will then spit out a couple of locations in your case, one for ubuntu, one for SUSE.  ie. (hd0,0) and (hd0,1) for example.

Then enter ```
root (hd0,0)
``` or where ever your ubuntu grub is

Then install the instructions to the MBR by using ```
setup (hd0)
```

Then type quit to exit grub and reboot.

---

### Post by EugeneK on 2007-03-01
Thanks, y'all.

---

