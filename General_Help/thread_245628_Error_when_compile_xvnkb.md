---
title: "Error when compile xvnkb"
date: 2006-08-28
forum: General Help
---

### Post by Viet Tux on 2006-08-28
[FONT="Arial"]
Hi
I want to compile xvnkb from source but can't, i installed
```

sudo apt-get install make
sudo apt-get install gcc
sudo apt-get install build-essential
sudo mkdir /usr/X11R6/include
sudo ln -s /usr/include/X11 /usr/X11R6/include/X11
sudo apt-get install xorg-dev
[/FONT]
When run configure:
[code]
Checking uchar... no
Checking ushort... yes
Checking uint... yes
Checking ulong... yes
Checking dynamic linking loader... yes
Checking X11 lib... no

```

---

