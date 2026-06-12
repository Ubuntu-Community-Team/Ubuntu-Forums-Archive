---
title: "LUBUNTU Not is possible to choice an color to taskbar and window title ?"
date: 2020-07-20
forum: General Help
---

### Post by aug7744 on 2020-07-20
Where I can change the color of the taskbar and window title ? I wait to choice an color and not change color using themes.

---

### Post by guiverc on 2020-07-20
Try looking at the Lubuntu manual 

[https://manual.lubuntu.me/stable/5/5.1/lxqt-panel.html](https://manual.lubuntu.me/stable/5/5.1/lxqt-panel.html)

*Note: you didn't provide release details, so the manual will assume you're on the latest Lubuntu 20.04 LTS, or modern Lubuntu using LXQt*

---

### Post by aug7744 on 2020-07-21
Thanks.

---

### Post by aug7744 on 2020-07-29
I not see how to change the color of window title.
Where I need to configure it ?
Have details in Linux that need to be more simple.

---

### Post by guiverc on 2020-07-29
You haven't mentioned what release of Lubuntu you are using.

Currently supported releases of Lubuntu include two different desktops, and without release information I can't offer more than the manual. Window borders are set via openbox (modifying a theme maybe the easiest), Panel colors are controlled by the LXQt theme however  (assuming you're talking about a LXQt based release of Lubuntu, but without release details I cannot know what version of LXQt, or if you're running LXDE).

--

My current window theme is "*Lubuntu Round*", and the config (including colors) can be seen with

```
guiverc@d960-ubu2:/usr/share/themes/Lubuntu Round/openbox-3$   ls -la
total 48
drwxr-xr-x 2 root root 4096 Jul 26 11:39 .
drwxr-xr-x 3 root root 4096 Feb 14 15:50 ..
-rw-r--r-- 1 root root  258 Jul 18 03:45 close.xbm
-rw-r--r-- 1 root root  133 Jul 18 03:45 desk_toggled.xbm
-rw-r--r-- 1 root root  157 Jul 18 03:45 desk.xbm
-rw-r--r-- 1 root root  142 Jul 18 03:45 iconify.xbm
-rw-r--r-- 1 root root  172 Jul 18 03:45 max_toggled.xbm
-rw-r--r-- 1 root root  172 Jul 18 03:45 max.xbm
-rw-r--r-- 1 root root  160 Jul 18 03:45 shade_toggled.xbm
-rw-r--r-- 1 root root  136 Jul 18 03:45 shade.xbm
-rw-r--r-- 1 root root 4397 Jul 18 03:45 themerc
```

In the *themerc *the colors can be pretty easily seen, so I'd likely COPY that theme into a different directory & make changes to that alternate theme.  Openbox themes apply to both LXDE & LXQt releases of Lubuntu (*unlike panelswhich is release specific*)

---

### Post by ActionParsnip on 2020-07-29
It's the Openbox config. Lubuntu uses Openbox as the window manager. It's dead light and amazing. Loads of themes around too.

---

### Post by aug7744 on 2020-08-13
I am Linux begginer user and in moment see possible change the window title changing themes instead of edit theme files.
@guiverc
About your reply I will try when have more information about editing system files.
Thanks very much for reply.

---

