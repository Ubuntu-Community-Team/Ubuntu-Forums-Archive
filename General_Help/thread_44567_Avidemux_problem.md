---
title: "Avidemux problem"
date: 2005-06-26
forum: General Help
---

### Post by flamarro on 2005-06-26
Hi, i installed avidemux in my ubuntu, following a tread of our foruns, Every movie in xvid i load it gives me this error

Beware: no valid audio codec found!
Save ( A+V ) wil generate bad avi.
Save audio will work

As i saw in the avidemux site, it means that i'm short on audio codecs, but i have followded all the thing in ubuntuguide site as codecs concern, so, what i have to do more, do you know?

haaaa, another question. What do you use to make a dvd from 2 or 3 avi and put some subtitles too....

---

### Post by Sav on 2005-06-27
[QUOTE=flamarro]Hi, i installed avidemux in my ubuntu, following a tread of our foruns, Every movie in xvid i load it gives me this error

Beware: no valid audio codec found!
Save ( A+V ) wil generate bad avi.
Save audio will work

As i saw in the avidemux site, it means that i'm short on audio codecs, but i have followded all the thing in ubuntuguide site as codecs concern, so, what i have to do more, do you know?

haaaa, another question. What do you use to make a dvd from 2 or 3 avi and put some subtitles too....[/QUOTE]

Installing avidemux, the system check for development libraries.
So, you have to install the libraries for ac3, mp3, vorbis and son on.

---

### Post by sapo on 2005-06-27
[QUOTE=flamarro]Hi, i installed avidemux in my ubuntu, following a tread of our foruns, Every movie in xvid i load it gives me this error

Beware: no valid audio codec found!
Save ( A+V ) wil generate bad avi.
Save audio will work

As i saw in the avidemux site, it means that i'm short on audio codecs, but i have followded all the thing in ubuntuguide site as codecs concern, so, what i have to do more, do you know?

haaaa, another question. What do you use to make a dvd from 2 or 3 avi and put some subtitles too....[/QUOTE]

i have the same problem here.. the solution i ve found was to save audio and then just add the audio later without reencoding it..

for dvds i use tovid, but it doesnt support external subtitles:

[http://tovid.sourceforge.net](http://tovid.sourceforge.net)

you could try this guide too:

[http://www.videohelp.com/forum/viewtopic.php?t=242455](http://www.videohelp.com/forum/viewtopic.php?t=242455)

---

### Post by flamarro on 2005-06-27
[QUOTE=Sav]Installing avidemux, the system check for development libraries.
So, you have to install the libraries for ac3, mp3, vorbis and son on.[/QUOTE]

Sorry, what do you mean by that? When i installed avidemux i followed a gui in forum, that did say to pay attention in some lines at the end of the installation. there were severel No's concerning some codecs, but as i followed the ubuntuguide i thought i have the codecs installed. I can see the movies and hear them. I supose it's a lilttle like FFDSHOW, once installed, we can see the movie, but to codify we need really the codec.
How can i install the libraries to for exemple AC3????
Sorry if i am making some kid questions.  :)

---

### Post by steven_ellis on 2005-06-27
Ok you need to make sure you have all of the correct development libraries for the audio codecs you want to use.

Hence things like libvorbis-dev and libmad-dev are needed for Ogm and MP3 audio.


Try the following

apt-get install  libmad0-dev liba52-dev libvorbis-dev libmjpegtools-dev libxvidcore4-dev libfreetype6-dev libxml2-dev libasound2-dev libsdl-dev libfaac-dev libfaad2-dev

And then rebuild avidemux.

Steve

---

### Post by Sav on 2005-06-28
[QUOTE=flamarro]Sorry, what do you mean by that? When i installed avidemux i followed a gui in forum, that did say to pay attention in some lines at the end of the installation. there were severel No's concerning some codecs, but as i followed the ubuntuguide i thought i have the codecs installed. I can see the movies and hear them. I supose it's a lilttle like FFDSHOW, once installed, we can see the movie, but to codify we need really the codec.
How can i install the libraries to for exemple AC3????
Sorry if i am making some kid questions.  :)[/QUOTE]

The first time I installed avidemux2, I made the same mistake.
But, as Steven wrote, avidemux checks for development libraries of the codecs, not for the codecs themselves.

---

### Post by flamarro on 2005-06-28
[QUOTE=steven_ellis]Ok you need to make sure you have all of the correct development libraries for the audio codecs you want to use.

Hence things like libvorbis-dev and libmad-dev are needed for Ogm and MP3 audio.


Try the following

apt-get install  libmad0-dev liba52-dev libvorbis-dev libmjpegtools-dev libxvidcore4-dev libfreetype6-dev libxml2-dev libasound2-dev libsdl-dev libfaac-dev libfaad2-dev

And then rebuild avidemux.

Steve[/QUOTE]


Perfect. That's just it.  
Thank you guys for your help.
How the hell do you discover this????

I'm begining to be afraid of one thing. That's so much things that i've done with the help of this forum. If i have to format and start installing ubuntu again, i don't know if i can make the same thing all over again.....

---

