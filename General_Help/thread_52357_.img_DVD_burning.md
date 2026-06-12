---
title: ".img DVD burning?"
date: 2005-07-27
forum: General Help
---

### Post by Phixion on 2005-07-27
Hello, how would I go about burning a .img in Ubuntu? Is there a certain program I need? I'm using Gnomebaker for my normal cd and dvd burning, but it doesn't support  .img files, it supports .iso though.

Thanks.

---

### Post by GrammatonCleric on 2005-07-30
I use "growisofs" which is included in the dvd+rw-tools package.


sudo apt-get install dvd+rw-tools


Then to burn the image...

(the /dev/dvd is would be where your dvd drive is (i.e. mine is /dev/hdc)



growisofs -dvd-compat -Z /dev/dvd=/path/to/image/foo.img



hope this helps.


GC

---

### Post by rizzyc on 2006-01-02
is there any gui program method of doing this like in Gnome Baker??

---

### Post by kingsidy on 2006-01-02
k3b

---

### Post by dudus on 2006-02-12
[QUOTE=GrammatonCleric]I use "growisofs" which is included in the dvd+rw-tools package.


sudo apt-get install dvd+rw-tools


Then to burn the image...

(the /dev/dvd is would be where your dvd drive is (i.e. mine is /dev/hdc)



growisofs -dvd-compat -Z /dev/dvd=/path/to/image/foo.img



hope this helps.


GC[/QUOTE]


Not so sure about this parameters... you should add the -dvd-video and spped flags... so it looks something like this:


```
growisofs -dvd-compat -speed=1 -Z /dev/dvd -dvd-video /path/to/image/foo.img
```

I wish I knew the parameter to set the volume name. Maybe it's -V but I'm not sure.

```
growisofs -dvd-compat -speed=1 -V VOLUME_NAME -Z /dev/dvd -dvd-video /path/to/image/foo.img
```

If someone knows more about the growisofs parameters please let us know.

---

