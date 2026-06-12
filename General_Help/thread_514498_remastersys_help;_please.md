---
title: "remastersys help; please"
date: 2007-07-31
forum: General Help
---

### Post by dragonwings on 2007-07-31
ok made custom iso with remasrersys it boots as live cd with all my stuff on it
it installs to hard drive fine
but when i try to boot hard drive it loads grub then gos to next stage (loading bar) and stops there .

---

### Post by dragonwings on 2007-08-01
help anyone out there ???

---

### Post by javi2401 on 2008-04-02
Why don't you try re-installing grub? For doing this, you have boot with an Ubuntu liveCD, then open a console, then type 
sudo grub
root (hd**X**,**Y**)
setup (hd**X**)
quit

Where **X** is the number of your hard disc, starting from 0 and 
**y**is the number of partition where Ubuntu is installed, for example if you write root (hd0,4) it is the same as hda5 (the fifth partition of your first hard disc) and so on

---

