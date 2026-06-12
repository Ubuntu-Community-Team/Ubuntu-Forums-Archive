---
title: "Resizing multiple (50+) videos"
date: 2005-06-13
forum: General Help
---

### Post by Trickyphillips on 2005-06-13
I have more than 50 avi video files that need to be resized. Avidemux seems to be a popular program for modifying video, but can it do multiple videos at once? If not, what would be a good choice of software for this type of task?

Thanks.

---

### Post by diebels on 2005-06-13
[QUOTE=Trickyphillips]I have more than 50 avi video files that need to be resized. Avidemux seems to be a popular program for modifying video, but can it do multiple videos at once? If not, what would be a good choice of software for this type of task?

Thanks.[/QUOTE]
 A good choice of software would be a shell script.

---

### Post by Trickyphillips on 2005-06-13
[QUOTE=diebels]A good choice of software would be a shell script.[/QUOTE]

Correct me if I'm wrong, but shell scripts can't control programs with GUIs, correct? If they can't, I don't need one, as I can just do something like "program-name --resize 640x480 *.avi" with a terminal-based application. :)

---

### Post by ow50 on 2005-06-14
Write a shell script that uses mencoder
[http://www.mplayerhq.hu/DOCS/HTML-single/en/MPlayer.html#menc-feat-rescale](http://www.mplayerhq.hu/DOCS/HTML-single/en/MPlayer.html#menc-feat-rescale)

---

### Post by Trickyphillips on 2005-06-15
[QUOTE=ow50]Write a shell script that uses mencoder
[http://www.mplayerhq.hu/DOCS/HTML-single/en/MPlayer.html#menc-feat-rescale](http://www.mplayerhq.hu/DOCS/HTML-single/en/MPlayer.html#menc-feat-rescale)[/QUOTE]

Thanks. :)

---

