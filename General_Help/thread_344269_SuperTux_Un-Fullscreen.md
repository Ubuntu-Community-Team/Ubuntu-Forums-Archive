---
title: "SuperTux Un-Fullscreen"
date: 2007-01-22
forum: General Help
---

### Post by Dr Small on 2007-01-22
Hello, I have SuperTux, or which i installed via the repository, and i don't have a good video card, so it won't play supertux in full screen mode.
But, is there some key combination, or command I can type when running the application to take it out of fullscreen mode?

Any help would be a appreciated.

Dr Small

---

### Post by Dr Small on 2007-01-22
..:: Bump ::..
If anyone could help, I would greatly appreciate it. :)

---

### Post by Dr Small on 2007-01-22
..:: Bump Bump ::..
I know this can't be totally impossible.
Come on. I would really like some help!

Dr Small

---

### Post by msak007 on 2007-01-25
You can run SuperTux in windowed mode using 1 of 2 ways:

1. If the game starts at all, go to the "Options" menu and uncheck "Fullscreen". 
2. Start it from a terminal and pass it the windowed flag (-w or --windowed):
```
supertux --windowed 
```or
```
supertux -w
```

---

### Post by Dr Small on 2007-02-09
I figured it out, but for the record of anyone else having this problem, I write unto you.

I tried:
```
supertux -w
```
but that didn't work, so after browsing through my /home/myusername I found .supertux
Example:
/home/drsmall/.supertux

In here I found "config" file, opened it with gedit, and found:

```

	;; the following options can be set to #t or #f:
	(fullscreen #t)
```

So, I changed the #t to #f and SuperTux was now Windowed when bringing it up, instead of fullscreen :)

Dr Small

---

