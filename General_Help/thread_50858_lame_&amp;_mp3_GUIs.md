---
title: "lame &amp; mp3 GUIs"
date: 2005-07-21
forum: General Help
---

### Post by Ferio on 2005-07-21
Are there GUIs for lame or mp3gain? I need to "work" with loads and loads of .mp3 and I hate doing it with the command line.

---

### Post by basbd on 2005-07-23
[QUOTE=Ferio]Are there GUIs for lame or mp3gain? I need to "work" with loads and loads of .mp3 and I hate doing it with the command line.[/QUOTE]
 Grip <http://nostatic.org/grip/> is a great GUI front end to lame, as well as many other mp3 encoders (toolame, bladeenc, mp3encode).

---

### Post by Ferio on 2005-07-23
OK, I've just installed it, it seems not very user-friendly, but very complete, thank you!

---

### Post by doclivingston on 2005-07-23
For ripping, Grip works well. When using mp3gain on lots of files, I think that the command line if the best way of doing it. A couple of days ago I ran `find /media/data/music -name '*.mp3' -print0 | xargs -0 mp3gain -r`, which automagically located my mp3 files and used mp3gain on them - which to me is much easier than doing it in a GUI (although it requires some knowledge of the command line).

---

### Post by tabinin on 2005-12-03
[QUOTE=doclivingston] I ran `find /media/data/music -name '*.mp3' -print0 | xargs -0 mp3gain -r`, which automagically located my mp3 files and used mp3gain on them - which to me is much easier than doing it in a GUI (although it requires some knowledge of the command line).[/QUOTE]

This is exactly what I have been looking for and is works like a charm.  Thank you!  I did add the -p (preserve time stamp) and -c (ignore clipping warning) options.

---

