---
title: "Rhythmbox won't import"
date: 2005-10-08
forum: General Help
---

### Post by redbull on 2005-10-08
I have Rhythmbox installed with AAC support, and it does find some of them in my library. But about 400-500 songs (AAC) are missing, and even if I tell the program to look specifically in a folder, it still refuses to import? Anyone with the same problem?

---

### Post by redbull on 2005-10-11
Help

---

### Post by shandar on 2005-10-11
Just a theory, are they protected or somehow damaged?

---

### Post by redbull on 2005-10-12
No, the files aren't damaged, and nothing is protected or from the iTunes music store.

---

### Post by zenwhen on 2005-10-12
Not that this helps, but I cannot get it to import my music either. It isn't a bad program, but it is very picky about importing.

---

### Post by bvc on 2005-10-15
all I can say is.....install every gstreammer pkg and import in small amounts

---

### Post by doclivingston on 2005-10-15
To import AAC files the package you need is "gstreamer0.8-faad" which is in multiverse, it doesn't work with protected files though.

If it's installed and still isn't working, can you try running the following from a terminal ```
gst-launch-0.8 playbin uri=file:///path/to/file.m4a
```

---

### Post by zrothe on 2005-10-16
I can't get it to import mp3s. It only imports my ogg files.

---

### Post by doclivingston on 2005-10-17
[QUOTE=zrothe]I can't get it to import mp3s. It only imports my ogg files.[/QUOTE]

The package you need is "gstreamer0.8-mad". However it's probably easier to install "gstreamer0.8-plugins" (and "gstreamer0.8-plugins-multiverse" is you have multiverse enabled), which will give you all the available gstreamer plugins.

---

### Post by zrothe on 2005-10-17
Ah ok, mp3s work now but still no wma. From what I read there doesn't seem to be a resolution or workaround for that problem.

---

### Post by doclivingston on 2005-10-17
[QUOTE=zrothe]Ah ok, mp3s work now but still no wma. From what I read there doesn't seem to be a resolution or workaround for that problem.[/QUOTE]

I can play most of my wma files by installing "gstreamer0.8-ffmpeg" (universe), there are a couple that don't work though.

---

