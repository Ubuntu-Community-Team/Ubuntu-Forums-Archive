---
title: "How to check if Headphones with microphone are working..."
date: 2021-02-24
forum: General Help
---

### Post by petrogromovo on 2021-02-24
[HR][/HR]Hello,
When I attach my Headphones with microphone to my Kubuntu 18 and try to make a test in skype
I have doubts if my text is realy written using microphone of my Headphones as I hear some noise in the background.
Are there some applicatiobs where I can check in text is writeen with  built-in mic or microphone of my Headphones?
I opened “Audio Volume Settings” but did not find such options...
I have MSI GP70 2PE Leopard...

Thanks!

---

### Post by HermanAB on 2021-02-24
Well, you can try sox, rec and play.

---

### Post by petrogromovo on 2021-02-25
Do you mean this app : 
> 
SoX is a command line utility that can convert various formats of computer
audio files in to other formats. It can also apply various effects to these
sound files during the conversion. As an added bonus, SoX can play and record
audio files on several unix-style platforms.

SoX is able to handle formats like Ogg Vorbis, MP3, WAV, AIFF, VOC, SND, AU,
GSM and several more.
Any format support requires at least libsox-fmt-base. Some formats have their
own package e.g. mp3 read and write support is provided by libsox-fmt-mp3.

SoX supports most common sound architectures i.e. Alsa, Libao, OSS and Pulse
(respectively provided by libsox-fmt-alsa, libsox-fmt-ao, libsox-fmt-oss and
libsox-fmt-pulse). It also supports LADSPA plugins.

?

---

### Post by HermanAB on 2021-02-25
Sox is a Swiss Army Knife for sound.

$ sudo apt install sox

Then in the simplest way:
$ rec filename
$ play filename

---

### Post by petrogromovo on 2021-02-25
Thanks! And of which tyupe filename must be ? You see usually I check of microphone in Headphones with skype - it have testing service for that : I say some text and  listen to it later.
Not sure how sox can be used here?

---

### Post by timgood on 2021-02-25
Give it any filename you like. e.g.:
$ rec mytestfile

Then record some words.
Then:
$ play mytestfile

... and you should be able to hear if your recording has worked.

---

