---
title: "Totem DVD Player doesn't seem to want to play my disc!"
date: 2005-11-02
forum: General Help
---

### Post by monomaniacpat on 2005-11-02
Hi guys,

First of all, apologies if this comes up a lot on the forum, I'm a total noob.

I've just installed breezy and the first problem I have encountered is that Totem doesn't seem to want to play my DVD. It makes a lot of whirring noises and accesses the drive quite a bit, but doesn't seem to actually start the DVD. What should I do?

Thanks in advance,

Mono.

---

### Post by Kyral on 2005-11-02
DVD Playback is NOT in Ubuntu by default. To enable it look here

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by monomaniacpat on 2005-11-02
Wicked, thanks. I can't seem to access the ubuntu website right now though - is it down at the moment? Could you copy and paste the contents? Cheers,

Mono.

---

### Post by bionnaki on 2005-11-02
totem will always suck.
dont use it.
use gxine or vlc instead.

---

### Post by Kyral on 2005-11-02
[QUOTE=bionnaki]totem will always suck.
dont use it.
use gxine or vlc instead.[/QUOTE]
Totem is fine for somethings. Keep personal opinions (phrased that way) to a minimum please

---

### Post by monomaniacpat on 2005-11-02
[QUOTE=Kyral]DVD Playback is NOT in Ubuntu by default. To enable it look here

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)[/QUOTE]

OK, done that. It says: "dpkg: status database area is locked by another process"

Is that normal?

Also, I tried the following advice:

[http://ubuntuguide.org/#dvdplayback](http://ubuntuguide.org/#dvdplayback)

and it said: "Unable to lock the administration directory (/var/lib/dpkg) is another process using it?"

Again, is this right?

Thanks in advance!

Mono.

---

### Post by dbott67 on 2005-11-02
Are you trying to run Synaptic and apt-get in a terminal at the same time?

Make sure that you're only using one method (at a time) to install packages.

-Dave

---

### Post by monomaniacpat on 2005-11-02
OK scratch that, I now have DVD playback but its jerky as hell... little help? :D

I've tried the advice on DMA enabling, but when I try to access /dev/hdc it says there is no such file or directory... :?

---

### Post by dbott67 on 2005-11-02
Totem is also very jerky on my old slow antiquated P2-300.  I installed VLC (as bionnaki suggests) and it offers much better performance for me.

-Dave

---

### Post by ecobuntu on 2005-11-02
Off Topic-
Dave is that avatar you and a lady friend?

---

### Post by monomaniacpat on 2005-11-02
[QUOTE=dbott67]Totem is also very jerky on my old slow antiquated P2-300.  I installed VLC (as bionnaki suggests) and it offers much better performance for me.

-Dave[/QUOTE]

I've downloaded VLC (I think) and its totally infathomable - how do I just run a DVD!?:p

---

### Post by ecobuntu on 2005-11-02
[QUOTE=monomaniacpat]I've downloaded VLC (I think) and its totally infathomable - how do I just run a DVD!?:p[/QUOTE]

I would like to suggest downloaded Kaffeine.  I think Kaffeine works real well.  I've never had problems with it.  
Good Luck!

---

### Post by RAOF on 2005-11-03
[QUOTE=monomaniacpat]OK scratch that, I now have DVD playback but its jerky as hell... little help? :D

I've tried the advice on DMA enabling, but when I try to access /dev/hdc it says there is no such file or directory... :?[/QUOTE]
Is /dev/hdc your DVD drive?  Because that's only an example.  Your drive may be /dav/hda,hdb,etc.  You probably have a link /dev/dvd.  If you go ls -lah /dev/dvd, that should say something like
```

ls -lah /dev/dvd
lrwxrwxrwx  1 root root 3 Nov  3  2005 /dev/dvd -> hda

```
showing that in my case, my dvd drive is /dev/hda

Oh, and VLC has an awful interface, yeah.  But to play a dvd, you want to go File -> Play Disc, and just accept the defaults

---

