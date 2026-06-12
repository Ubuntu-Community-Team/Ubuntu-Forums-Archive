---
title: "Help with an mms stream"
date: 2007-01-24
forum: General Help
---

### Post by zupermanz on 2007-01-24
I use ubuntu 6.10 and i cant play a certain mms. mms://85.17.2.144/sportfm7712
I have tried with totem (with xine and gstreamer) amarok and others but i havent had any result...
With almost any other streams i havent had any problem....

Thanks in advance.

---

### Post by Laerte Andrade on 2007-01-27
Hey, I've tried it in my system (gstreamer 0.10 with all possible plug-ins installed, including w32codecs) and it won't work too. I'm having this same problem with a radio I used to listen a lot:

mms://videos.tvcultura.com.br/fm
[http://www.tvcultura.com.br/radiofm/radiofm.asx](http://www.tvcultura.com.br/radiofm/radiofm.asx)

Oh, well.  :-({|=

---

### Post by vyruss on 2007-03-09
> **zupermanz said:**
> I use ubuntu 6.10 and i cant play a certain mms. mms://85.17.2.144/sportfm7712
I have tried with totem (with xine and gstreamer) amarok and others but i havent had any result...
With almost any other streams i havent had any problem....

Thanks in advance.

VLC Media Player plays it fine!

And move to 6.10 ;)

---

### Post by panch0 on 2007-03-09
Even better than VLC is MPlayer (KPlayer is the frontend I use). Just install it and run:

mplayer mms://videos.tvcultura.com.br/fm

I actually tried it a second ago, and it plays fine in KPlayer. The station is called "Radio Cultura FM - Sao Paulo".

---

### Post by zupermanz on 2007-03-19
VLC does not play it at all.

Mplayer buffers, plays nothing for 11 sec (always 11 seconds) and then quits


Any other ideas?

---

### Post by panch0 on 2007-03-19
Upgrade MPlayer to 1.0rc1. Like I said it played your stream fine for me.

---

