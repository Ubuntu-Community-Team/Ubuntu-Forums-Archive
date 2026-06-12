---
title: "another problem with realplayer10"
date: 2005-06-10
forum: General Help
---

### Post by hrvoje-pula on 2005-06-10
hi again

please don't be mad at me, i'm new in linux but i try to learn.

when i try to play avi fili or mpg file with RP it says **The player does not have capabillities to play back this content** ... check for update.

how to get update?

thanx

---

### Post by frodon on 2005-06-10
I think it's because you don't install libraries for avi, mpeg.

The simple way to have a good player (for me) is to install all libraries (quicktime, avi, mpeg, dvd,RP, ...), and install totem-xine or xine-ui or gxine, so you can read all videos using only one player (even realplayer videos).
Personaly I prefer totem-xine.
.
Install these libraries if didn't do it yet : w32codecs, libdvdcss2 and also quicktime, you can find them in synaptic or you can read this : [http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs).

---

### Post by hellraiser_rob on 2005-06-10
sorry to hijack the thread, but i'm also having problems with realplayer, basically i tried installing it two different ways, firstly with apt-get and then directly downloading the bin file from real.com.  However both times the app wouldn't run after a successfull installation!!!

---

### Post by frodon on 2005-06-10
you don't find it in synaptic ? It's the better way to install it (more simple).
you must add repositories in your sources.list file if you can't find it actualy in synaptic.

---

### Post by hellraiser_rob on 2005-06-10
sorry i don't think i explained it very well

its installed fine

it just won't run when i launch it

---

### Post by frodon on 2005-06-10
ok
Launch RP within a terminal, and post the result, it's the only way to know why it doen't work.

---

### Post by hrvoje-pula on 2005-06-10
check this out 

[http://www.ubuntuforums.org/showthread.php?t=32063](http://www.ubuntuforums.org/showthread.php?t=32063)

it realy helps.
 
good luck

---

### Post by Musashi on 2005-06-14
[QUOTE=hellraiser_rob]sorry i don't think i explained it very well

its installed fine

it just won't run when i launch it[/QUOTE]

Do a "sudo killall esd" in a terminal before launching RealPlayer

---

