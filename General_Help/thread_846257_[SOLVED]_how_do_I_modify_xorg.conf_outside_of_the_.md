---
title: "[SOLVED] how do I modify xorg.conf outside of the gui?"
date: 2008-07-01
forum: General Help
---

### Post by hurtstotalktoyou on 2008-07-01
Hey, all.

Whenever I install fluxbuntu 7.10 on an old covington system, all I get on the first boot is a scrambled screen.  This does not seem to be a problem with fluxbuntu alone, as I have the same problem with vectorlinux 5.9 light.

Now, I know that with the right xorg.conf settings my system will work.  The problem is, I need to be able to change it without booting into the gui (because I *can't* boot into the gui).  How do I do that?

Thanks!

---

### Post by sisco311 on 2008-07-01
First backup the file:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
```Use nano to edit the file:
```
sudo nano /etc/X11/xorg.conf
```Ctrl+o, Enter to save
Ctr+x to exit
(or Ctrl+x, Y, Enter to save and exit)

to restore the original file:

```
sudo cp /etc/X11/xorg.conf-backup /etc/X11/xorg.conf
```

---

### Post by avtolle on 2008-07-01
Since you are using 7.10, from the command line```
sudo dpkg -reconfigure xserver-xorg
```

---

### Post by hurtstotalktoyou on 2008-07-02
> **sisco311 said:**
> First backup the file:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
```Use nano to edit the file:
```
sudo nano /etc/X11/xorg.conf
```Ctrl+o, Enter to save
Ctr+x to exit
(or Ctrl+x, Y, Enter to save and exit)

to restore the original file:

```
sudo cp /etc/X11/xorg.conf-backup /etc/X11/xorg.conf
```

Worked like a champ, thanks!  I had forgotten about nano.

---

