---
title: "imediate cd ripping?"
date: 2005-08-31
forum: General Help
---

### Post by navilon on 2005-08-31
[SIZE=4][FONT=Verdana]is it possible to auto mount an audio cdrom, have it find album data from freeDB, rip tracks to the drive using the FLAC codec, and eject the cd when its done, all automated?[/FONT][/SIZE]

---

### Post by tehwa on 2005-08-31
You might like to take a look at an application named gnome-baker

```
sudo apt-get install gnome-baker
```

It autodetects CDROM, finds track data, so all you need to do is hit the copy button. By default it uses .ogg, but you can easily change this to FLAC.

---

### Post by vruum on 2005-08-31
[grip](http://nostatic.org/grip/) will do all these things, it should be in synaptic.

---

### Post by miscreant on 2005-11-28
[QUOTE=vruum][grip](http://nostatic.org/grip/) will do all these things, it should be in synaptic.[/QUOTE]

Looks like that's a graphical client. That might answer the OP, but does anyone know if there is a command line type daemon program that will do this?

I basically want to be able to just put a CD into my linux server, have it copy the tracks to a directory shared via samba and eject the CD.

My wife is not going to want to log into linux to figure this out, but after the whole Sony DRM fiasco, I want her to be able to put the CD into the server, have it rip the music and show up in Windows Media Player on her desktop and thus avoid virus like DRM programs.

Anybody have any ideas?

miscreant

---

### Post by HornedBeast on 2008-05-06
I am after the exact same thing. I would like my server to just accept discs, rip them (hopefully using ABCDE as I have that setup the way I like it), then eject the disk. No front-end required at all - just automated.

Any ideas?

---

