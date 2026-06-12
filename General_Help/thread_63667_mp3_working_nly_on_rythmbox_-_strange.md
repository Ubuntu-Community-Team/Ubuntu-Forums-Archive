---
title: "mp3 working nly on rythmbox - strange"
date: 2005-09-08
forum: General Help
---

### Post by boskifelippe on 2005-09-08
Hello,
To begin with, i will say that YES i've done everything to enable mp3 playing on my ubuntu that was written it the guide. i've downloaded the codecs, as well as xmms and beep-player.
and here goes the strange part.
my mp3 will only go under the rythmbox. when i try to play them with xmms or beep the program freezes and i have to kill it.
but as you probably know rythmbox sux, because it doesn't support 'search' option and so on.
i was wondering is it possible this could be a case of the sound device driver? my motherboard is epox rda3i with nforce 2
any ideas?
thx a lot.

---

### Post by ngnr on 2005-09-08
Hello, i think you have to download the proper xmms plugins, because the ubuntuguide refers to gstreamer engine plugins.

System  -> Administration -> synaptic 

then search for "xmms-" 

you will find plugins for mp4 , mp3, flac , etc that should work.

by the way , if you have a large music collection i suggest you to use, rithymbox, amarok, Quod libet.

sorry for my english.

Good luck.

---

### Post by Wolki on 2005-09-08
[QUOTE=boskifelippe]and here goes the strange part.
my mp3 will only go under the rythmbox. when i try to play them with xmms or beep the program freezes and i have to kill it.
[/QUOTE]

Start xmms/bmp without playing a file. Go to the preferences window and set output to esd. It should work now.

What Search feature are you missing in rhythmbox? I'm not using it but I'm not sure xmms will have it if rb doesn't.

---

### Post by boskifelippe on 2005-09-08
[QUOTE=Wolki]Start xmms/bmp without playing a file. Go to the preferences window and set output to esd. It should work now.

What Search feature are you missing in rhythmbox? I'm not using it but I'm not sure xmms will have it if rb doesn't.[/QUOTE]

omg - that was a bullseye
thx a lot m8 and sorry for bothering you with such an easy one.
and about that 'search' - i didn't find 'search for the mp3 by title'-some option. but luckly xmms supports it :D

---

