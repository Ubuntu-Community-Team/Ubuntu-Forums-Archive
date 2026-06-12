---
title: "ubuntu not booting; how to install apt"
date: 2008-01-28
forum: General Help
---

### Post by 3kravinarayan on 2008-01-28
my hard disc has been corrupted due to a power failure.  When I boot it says apt not found - type "apt-get install apt" but when I do this it says apt not found.  Can anybody tell me how to recover and get apt and start ubuntu, please

:guitar:

---

### Post by FuturePilot on 2008-01-28
The partition may need a fsck
Try booting up the live CD and running
```
sudo fsck -C /dev/sdXY
```
Replace XY with whatever the partition is like sda1 for example.
Make sure the drive is ** not** mounted

---

### Post by Majorix on 2008-01-28
If that doesn't work, get the .deb for apt from packages.ubuntu.com and install it using dpkg. Like this:
```
sudo dpkg -i apt #or whatever the package name is
```

---

### Post by 3kravinarayan on 2008-01-28
thanks but did not work.

I have dual boot system with a share partition and a swap.  I don't know if this is the problem.  It is asking me to run E2fsck.  Please tell me how to do it

thanks.:guitar:

---

### Post by 3kravinarayan on 2008-01-28
sudo fsck -C /dev/sdXY  from live CD worked  Thanks so much


:guitar:

---

