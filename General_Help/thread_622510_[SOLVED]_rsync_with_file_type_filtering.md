---
title: "[SOLVED] rsync with file type filtering?"
date: 2007-11-24
forum: General Help
---

### Post by kaiju on 2007-11-24
hi

i'm using this "custom action" in thunar to copy music folders to my iriver t60:
```
xterm -e rsync -rvtW --delay-updates --modify-window=1 %F /media/disk/Music/
```
i often keep images and text or pdf files in my music directories, but only need the mp3/ogg files on the music player. given the slow usb port of my almost-ten-year-old machine, filtering would also speed up the transfer a bit :)

is there any way to alter the command to make rsync only act on the mp3/ogg files in the directory?

---

### Post by kaiju on 2007-12-05
after some asking around, i finally got helped out at the romanian ubuntu forum ([http://forum.ubuntu.ro](http://forum.ubuntu.ro)).

in case anybody wants to achieve something similar, the solution in my case was:

```
rsync -rvtW --delay-updates --modify-window=1 --progress --include='*.mp3' --include='*.ogg' --exclude='*.*' <source> <dest>
```

---

