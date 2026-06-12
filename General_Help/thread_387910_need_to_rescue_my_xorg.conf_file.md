---
title: "need to rescue my xorg.conf file"
date: 2007-03-18
forum: General Help
---

### Post by Athanasius on 2007-03-18
I just reformatted and got everything working well except for the resolution.  I try that and I fry my xorg.conf file.  I am now using the live disk to try to rescue things.

I managed to mount my hard drive but it will only show my home directory when I need to get into /etc/X11/xorg.conf  

please help, I need to fix this tonight

---

### Post by Kateikyoushi on 2007-03-18
You could boot recovery mode to edit your xorg.

---

### Post by The Noble on 2007-03-18
You can still boot into the hard drive in single user mode right? If you can, you will see the command line and then you can fix X. When in command line, type:
```

sudo nano /etc/X11/xorg.conf

```
To fix it. Or, if you want to start from scratch, type:
```

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by roachk71 on 2007-03-18
I believe (if you want a default configuration without the hassle), you should use

```
dpkg-reconfigure -phigh xserver-xorg
```
in recovery mode.

Note that on some hardware, though, it may give a slower card configuration.

---

### Post by Athanasius on 2007-03-18
Here is what I did to fix the issue:

I booted the live disk & mounted my sda2 partition.  Then I copied the xorg.conf file from the live disk and pasted it to my home directory (the only directory on my hard disk that I could get a hold of).  then I rebooted into safe mode and copied over my corrupted xorg file.  Reboot and it all worked.  It turns out that the command that I wanted from the beginning was ```
sudo dpkg-reconfigure xserver-xorg
```
crisis averted! until the next one.  I hope somebody will learn from this as I did :)

---

