---
title: "WMA video to OGG conversion possible??"
date: 2005-05-30
forum: General Help
---

### Post by uberlinux on 2005-05-30
I have a bunch of videos made with WMA that I want to convert to ogg, and I cant find any howtos anywhere; does anyone know what it takes to do this?

---

### Post by Marquis_de_Carabas on 2005-05-30
[QUOTE=uberlinux]I have a bunch of videos made with WMA that I want to convert to ogg, and I cant find any howtos anywhere; does anyone know what it takes to do this?[/QUOTE]

Transcode seems to be the primary choice for converting video files. The April 2005 issue of Linux Magazine has a lengthy tutorial on it if you can get hold of a copy, otherwise I'm sure there's plenty of information on the web. [The Transcode homepage](http://www.transcoding.org) is as good a place to start as any.

Converting WMA audio files to Ogg is a lot simpler. Transcode will do this, but I just use a simple shell script.

---

### Post by uberlinux on 2005-05-30
now if only transcode worked without all those dependancies, but thanks for giving me a place to start.

---

### Post by Marquis_de_Carabas on 2005-05-30
[QUOTE=uberlinux]now if only transcode worked without all those dependancies, but thanks for giving me a place to start.[/QUOTE]

Hmm, I thought it was in the repositories but a quick apt-cache search shows that it's not. Although, for no readily apparent reason, gtranscode is.

You could also try Mencoder. That is definitely in the repositories, and should do the job.

(Edit: Alternatively, Transcode is in the Marillat repository)

---

