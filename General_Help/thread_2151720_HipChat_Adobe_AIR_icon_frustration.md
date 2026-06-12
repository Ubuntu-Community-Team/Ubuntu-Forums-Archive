---
title: "HipChat: Adobe AIR icon frustration"
date: 2013-06-05
forum: General Help
---

### Post by TWj2X6Ln4F on 2013-06-05
Hello All,

I use a program called HipChat at work that is an Adobe AIR app. I have used the Windows version without trouble, but on when on linux the system tray icon has a white background, rather than a transparent background. This makes for a rather unpleasent look.

I have uncompressed the .air file and it seems all icons inside the .air file are transparent pngs. After installing the .air file, I ran:

find / -name "*hipchat*"

and deleted all image files it returned to see what file the system tray was reference. Despite all the files being gone, the icon still remained.

This leads me to ask 3 things:

1) Maybe the file is named something that doesnt contain the term hipchat
2) Maybe the icon is embedded in the binary
3) Can anyone help at all?

Thanks!

---

### Post by kostkon on 2013-06-05
Have you tried the [native linux client]("https://www.hipchat.com/linux"), maybe you'll get better results and better perfomance.

---

### Post by TWj2X6Ln4F on 2013-06-06
Perfect! This works! Thanks!

---

### Post by TWj2X6Ln4F on 2013-06-06
Now how do I set this to solved?

---

