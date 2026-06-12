---
title: "Ubuntu 15.04 What bug is this and how can I report it."
date: 2015-07-28
forum: General Help
---

### Post by zemega on 2015-07-28
This might be late. I just upgraded from Ubuntu 14.10 to 15.04 64 bit. So there is this one bug I found and I do not know how to report it properly. When you open a gif using Image Viewer 3.14.4, you cannot open any other application. I tried opening gedit through terminal and this is what I got:

```
xxx@xxx:~$ gedit &
[1] 7349
xxx@xxx:~$ Maximum number of clients reached
** (gedit:7349): WARNING **: Could not open X display
Maximum number of clients reachedgdk_mir_display_open
Failed to connect to Mir: Failed to connect to server socket: No such file or directory
Unable to init server: Could not connect: Connection refused

(gedit:7349): Gtk-WARNING **: cannot open display: :0

[1]+  Exit 1                  gedit
xxx@xxx:~$ 
```

Upon closing the Image Viewer playing the gif file, I can open other application.
You may say this is Image Viewer specific, but I tried opening the gif file using Viewnor, ImageMagick and it gives the same thing. Even using Pinta gives the same result. So I was wondering if anyone running 15.04, or fresh 15.04 installation experiences the same thing. Below is the gif file, just for example sake.
[ATTACH=CONFIG]263434[/ATTACH]

---

### Post by zemega on 2015-07-28
Okay, screw this thread. Apparently its not the gif file. I was not able to reproduce this error.

---

