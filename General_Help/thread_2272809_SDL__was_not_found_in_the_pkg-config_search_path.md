---
title: "SDL  was not found in the pkg-config search path"
date: 2015-04-08
forum: General Help
---

### Post by Creatorr on 2015-04-08
I'm using Ubuntu 14.04 for implementation of Image Segmentation  algorithm on Pandaboard. So, I had installed SDL using following commands



```
hg clone https://hg.libsdl.org/SDL SDL
cd SDL
mkdir build
cd build
../configure
make
sudo make install
```

But, while running a simple program , its displays "SDL  was not found in the pkg-config search path".Herein I've attached screenshot of terminal window. So, please help in solving this error. [ATTACH=CONFIG]261179[/ATTACH]

---

### Post by mc4man on 2015-04-08
Probably because you're building sdl2 so folder & .pc name(s) would reflect that. 
Take a look in /usr/local/lib/ & /usr/local/include

---

### Post by Creatorr on 2015-04-10
Yes I was building sdl2
As I'm new to ubuntu I didn't get your point. So, can you please explain me through steps. Else, please refer any link.

---

