---
title: "Resize and rename multiple pics"
date: 2007-05-14
forum: General Help
---

### Post by jude999 on 2007-05-14
Hi all,

I have a hole bunch of pictures I need to resize to make them lighter. I would also like to rename them all in one time (eg. paris holiday 1, 2, 3...)

Is there a good program to do that?

Thanks

---

### Post by nikhilk on 2007-05-14
You can use [ImageMagik]("http://www.imagemagick.org/script/index.php") to do the resizing. A little script can combine the two operations.

---

### Post by Wim Sturkenboom on 2007-05-14
***jhead*** allows you to use the EXIF info (date and time) during the rename
```

jhead -n%Y%m%d_%H%M%S_paris_%f *.jpg

```
will create files like 20070311_103311_paris_img0001.jpg where img0001.jpg was the original filename.

It also allows you to change date/time if your camera was set incorrectly.

Not sure about resizing.

---

### Post by m.musashi on 2007-05-14
You might also check out [jalbum](http://jalbum.net/). I don't think it's FOSS but there is a version for Linux and it's free. I used the windows version. I don't know much about the linux one. It's mainly a tool for making web albums but it might also meet your needs. I know it will resize images but not sure about how flexible it is for renaming. It's been a while since I used it. It is a pretty nice program, though.

---

