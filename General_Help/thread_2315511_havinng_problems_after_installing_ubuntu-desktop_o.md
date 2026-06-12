---
title: "havinng problems after installing ubuntu-desktop on lubuntu"
date: 2016-02-29
forum: General Help
---

### Post by aman16 on 2016-02-29
I had lubuntu installed on my laptop. I installed ubuntu-desktop using synaptic and chose ubuntu at login. Some broken packages were found, I used synaptic to fix them. now I have two Bluetooth icons on the taskbar and every now and then a error message pops up saying system program problem found. I like ubuntu, and want to completely remove lubuntu with all its components like a regular ubuntu installation. Thanks in advance

---

### Post by X-RED_Tech on 2016-02-29
Duplicated icons and other things happen often when we add different desktops.
If you want plain Ubuntu why don't you just install it from scratch? Do you backups first, of course.

---

### Post by aman16 on 2016-02-29
do not have the resources to make a backup. unfortunately my entire harddisk is under my home folder. I have no idea how it happened. I think i did something wrong during installation.

---

### Post by aman16 on 2016-02-29
I will do that if there is no other way. Please help.

---

### Post by Bucky Ball on 2016-02-29
*Thread moved to **General Help**.*

```
sudo apt-get remove lubuntu-desktop
```

Have no idea of the consequences, but that is how you'd do it. After that, open a terminal and:

```
sudo apt-get autoremove
sudo apt-get install ubuntu-desktop
```

... the latter command to reinstall anything removing lubuntu-desktop may have inadvertently dragged out. Might work.

When you want to try a desktop environment, DON'T install *buntu-desktop. This is not the way to do it and a VERY common mistake. Ubuntu uses the Unity desktop environment. So install Unity. Xubuntu uses xfce4. If you want that, just install xfce4:

```
sudo apt-get install xfce4
```

Installing 'xubuntu-desktop' is more or less identical to installing Xubuntu on top of whatever OS you already have installed. This can cause unpredictable duplications and redundancies and general bloat, which you've discovered the hard way.

---

### Post by X-RED_Tech on 2016-02-29
Hummm... Isn't lubuntu-desktop a meta-package? If so it won't uninstall anything else but that package itself.

---

### Post by Bucky Ball on 2016-02-29
> **X-RED_Tech said:**
> Hummm... Isn't lubuntu-desktop a meta-package? If so it won't uninstall anything else but that package itself.

In that case, on to plan B. See what plan A offers to uninstall first though, I'd suggest. Then:

```
sudo apt-get autoremove
```

---

