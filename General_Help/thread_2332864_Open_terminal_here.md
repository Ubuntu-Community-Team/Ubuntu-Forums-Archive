---
title: "Open terminal here"
date: 2016-08-04
forum: General Help
---

### Post by 4kh3RAm on 2016-08-04
Does mate-terminal have an equivalent of this ?

The package manager does not have urxvt.
[h=2][SIZE=3]Open Terminal Here
[/SIZE][/h][SIZE=3] [/SIZE][SIZE=3]**Command:** [/SIZE]

urxvtc -cd %f

---

### Post by Dennis N on 2016-08-04
> The package manager does not have urxvt.
This is part of another package:
```
dmn@Sydney ~ $ urxvt -info
The program 'urxvt' can be found in the following packages:
 * rxvt-unicode
 * rxvt-unicode-256color
 * rxvt-unicode-lite
Try: sudo apt-get install <selected package>
```

---

### Post by 4kh3RAm on 2016-08-04
Thanks.

I found this too and added it as a custom action for thunar.

```
exo-open --working-directory %f --launch TerminalEmulator
```

---

