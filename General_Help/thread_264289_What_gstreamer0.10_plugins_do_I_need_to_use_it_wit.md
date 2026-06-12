---
title: "What gstreamer0.10 plugins do I need to use it with gmusicbrowser?"
date: 2006-09-24
forum: General Help
---

### Post by TeeAhr1 on 2006-09-24
I use gmusicbrowser with mpg321/ogg123/flac123/amixer, but I've got some flac files that flac123 keeps choking on, even though the files work elsewhere.  So in the interests of finding out what the issue is, I'd like to install gstreamer support so I can compare.  Problem is, I'm not sure exactly what gstreamer libraries I need to install for mp3, ogg, and flac support.  I need the 0.10 libraries, not 0.8.  If anyone could advise, I'd be most appreciative.  Thx!

-pete

---

### Post by bom28 on 2006-09-24
Well, gmusicbrowser being written in perl, it needs the gstreamer perl bindings (libgstreamer-perl), which are not in ubuntu dapper (I think it will be in edgy). So if you really want to use gmusicbrowser with gstreamer using dapper, you need to compile the bindings yourself, which can be a little challenging if you have never done this before.
But really, all flac files should be playable with flac123, what does it say when you run "flac123 file.flac" in a command line ?

---

