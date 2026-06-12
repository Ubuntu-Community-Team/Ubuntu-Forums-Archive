---
title: "make gtkpod write the metadata on hard drive audio, too, and not just iPod audio file"
date: 2006-08-06
forum: General Help
---

### Post by hanzj on 2006-08-06
Hello,
I've been adding id3 tags (metadata/song info) to several mp3s that I've added to gtkpod.I've added title, artist, album. When I press the sync button, these changes are reflected in the mp3s that are my iPod, but the copies on my hard drive are still unedited. How can I update the metadata (id3 tags) in the mp3s on my hard drive, too?

---

### Post by vwiggin on 2006-08-07
Hi,

You could use the commandline program id3v2 to edit the metadata directly on your harddrive, and then use gtkpod to sync with the iPod.

```
id3v2 -l foo.mp3
```

will tell you what tags are already there, and

```
id3v2 -f
```
will give you a rundown on all the possible tags.

As far as I can tell there is no recursive option, but you can always make a small loop, e.g.

```
for file in directory/*mp3; do id3v2 --TALB "Name of Album" --TCOM "Name of Composer" $file; done
```

\v

---

### Post by hanzj on 2006-08-07
Gtkpod is able to do this, I later found out.

The Edit tab in preferences has a checkbox to do this:

   "Write ID3 tags to disk when modified in gtkpod"

---

