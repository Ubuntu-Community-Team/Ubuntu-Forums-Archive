---
title: "totem problem"
date: 2005-09-27
forum: General Help
---

### Post by arlie on 2005-09-27
Everytime I try to play an mp3 files I get this error:

There were no decoders found to handle the stream in file "file:///home/arlie/Desktop/temp/Bisaya%20Rap%20RnB%20Mixx/01%20Gipasagdan%20sa%20kusina.mp3", you might need to install the corresponding plugins

Please help. What am I missing...

---

### Post by 23meg on 2005-09-27
you need to install the mp3 codec. "sudo apt-get install gstreamer0.8-lame" should do it. 

refer to [http://www.frankandjacq.com/ubuntuguide/5.04](http://www.frankandjacq.com/ubuntuguide/5.04) if you need further help.

---

### Post by arlie on 2005-09-27
[QUOTE=23meg]you need to install the mp3 codec. "sudo apt-get install gstreamer0.8-lame" should do it. 

refer to [http://www.frankandjacq.com/ubuntuguide/5.04](http://www.frankandjacq.com/ubuntuguide/5.04) if you need further help.[/QUOTE]

I still got the same error after installing gstreamer0.8-lame.

---

### Post by bob k on 2005-09-27
[QUOTE=arlie]I still got the same error after installing gstreamer0.8-lame.[/QUOTE]

try using xine as the backend

---

### Post by GazaM on 2005-09-27
lame is the mp3 'encoder'... the decoder plugin is gstreamer mad.

---

### Post by bob k on 2005-09-27
[QUOTE=23meg]you need to install the mp3 codec. "sudo apt-get install gstreamer0.8-lame" should do it. 

refer to [http://www.frankandjacq.com/ubuntuguide/5.04](http://www.frankandjacq.com/ubuntuguide/5.04) if you need further help.[/QUOTE]

I guess I missed that one. Looks better than the howto's.

It is now book marked

Bob

---

