---
title: "OGG to MP3"
date: 2006-07-21
forum: General Help
---

### Post by Ruben123 on 2006-07-21
How can you cenvert OGG to MP3, or just convert a cd to mp3, i converted my cd to ogg files, but my mp3 player can't play them, please help

greets

---

### Post by T700 on 2006-07-21
Have you installed the codecs for MP3's?  If not, go to the link for Automatix in my sig and run that.  After that, you should be able to use any ripping program or CD burner to rip/convert to MP3's.

Paul

---

### Post by Ruben123 on 2006-07-21
> **T700 said:**
> Have you installed the codecs for MP3's?  If not, go to the link for Automatix in my sig and run that.  After that, you should be able to use any ripping program or CD burner to rip/convert to MP3's.

Paul

I installed the GStreamer plugins from the "ugly" set, so thay sad in the tutorial, i can play mp3 files on my pc, that's ok, but i would like to confert to mp3, from cd or ogg, what program i need to use.

I tryed SoX to convert ogg to mp3, but that was not working

---

### Post by it.henrik on 2006-07-21
[http://www.igso.net/nkb/Converting_ogg_to_mp3_in_Linux](http://www.igso.net/nkb/Converting_ogg_to_mp3_in_Linux)

google is your friend

---

### Post by Ruben123 on 2006-07-21
> **it.henrik said:**
> [http://www.igso.net/nkb/Converting_ogg_to_mp3_in_Linux](http://www.igso.net/nkb/Converting_ogg_to_mp3_in_Linux)

google is your friend

Oh my god, what is that

what i need to do with the pl file

---

### Post by Ruben123 on 2006-07-21
I tink i have not the right codecs for MP3's, do you know what i need?

---

### Post by jongkind on 2006-07-21
A nice programme that may help you is Soundconverter. It is available in the repositories.

---

### Post by Ruben123 on 2006-07-21
> **jongkind said:**
> A nice programme that may help you is Soundconverter. It is available in the repositories.

this program looks fine, bit i can't select mp3, its light grai

---

### Post by jongkind on 2006-07-21
OK, you miss some codecs. If not installed yet I suggest that you install 
lame 
gstreamer0.8-lame
liblame0

---

### Post by Ruben123 on 2006-07-21
> **jongkind said:**
> OK, you miss some codecs. If not installed yet I suggest that you install 
lame 
gstreamer0.8-lame
liblame0

nope, i even coudn't fint the 3 files. so i installed everything that strats with gstreamer0.8

---

### Post by jongkind on 2006-07-21
gstreamer is not the problem, it's all about lame. The reason why you don't see these files in synaptic is that apparantly you did not enable all to repositories (including the Universe and multiverse repositories). I suggest you first try that. After this you should be able to install

lame
gstreamer0.8-lame
liblame0

---

### Post by Ruben123 on 2006-07-22
nope even if u enable & update, i can't find lame in the list, is there an other way to instal those stuf??

---

### Post by Soarer on 2006-07-22
LAME is in mulitverse. go: System > Administration > Synaptic Package Manager. When it loads, and after you put in your passwords, go to: Settings > Repositories, click the ADD buttom & put ticks in the two lower boxes, which currently do not have them. Back in the Synaptic main screen, click 'Relad' at the top/left.

Then search for LAME. Any problems, let us know.

Automatix is easier, as it sets up the repositories for you too.

---

### Post by Ruben123 on 2006-07-22
ok, everything is working now, thank you very much :D

greets

---

### Post by joseph_rothwell on 2008-03-26
I had this problem. I wanted to put music on my MP3 player.

Basically, download any windows software that converts OGG to MP3, and then download wine. Rune the program through Wine. Convert your files. Hey presto, you have MP3 files.

Put them on your MP3 player or whatever.

Worked for me, but then again, I have the codecs installed.

Good luck.

---

### Post by portach king on 2008-03-26
There's a progrm you can install via Synaptic and the Add/Remove application called Sound Converter. It works great, has a simple interface so it's very easy to use, and it works fast. Have fun.

---

