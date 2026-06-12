---
title: "sound conversion"
date: 2007-07-08
forum: General Help
---

### Post by Harkainos on 2007-07-08
I would like to convert some ogg files to mp3 so I can play them in my mp3 player.... I have tried soundconverter (1) and soundkonverter (2), but 1 doesn't convert to mp3 and 2 locks up anytime I want to convert anything.

Is there a solid sound converter out there?

---

### Post by dreadlord_chris on 2007-07-08
> **Harkainos said:**
> I would like to convert some ogg files to mp3 so I can play them in my mp3 player.... I have tried soundconverter (1) and soundkonverter (2), but 1 doesn't convert to mp3 and 2 locks up anytime I want to convert anything.

Is there a solid sound converter out there?

SoundKonverter works just fine here - what problem are you having?

---

### Post by Harkainos on 2007-07-08
I simply stops and sits at 0%. How would I run it in terminal? Maybe then it will post some errors.

---

### Post by kellsens on 2007-07-08
Hi Harkainos,

     there's a plugin on nautilus that convert WAV, OGG and MP3. To use it, install it from Synaptic or type on terminal :

$ apt-get install nautilus-script-manager nautilus-script-sound-converter

and, then enable it:

$ nautilus-script-manager enable ConvertAudioFile

That's it. Now, click with right button on your file and click Scripts > ConvertAudioFile, and choose the type of file you want.

*this answer was translated from [http://estudiolivre.org](http://estudiolivre.org) (sorry my english hehehe)*

Kellsens

---

### Post by Harkainos on 2007-07-08
I have that now. When I do run the script it only gives me FLAC and WAV options. How do I get the MP3 Option in there

---

### Post by jjross on 2007-07-08
I think you need 'lame' to convert to mp3
Try doing a search here on the forum for mp3 and lame and you should find out more about it.

---

### Post by kellsens on 2007-07-08
Hi, Harkainos !

     Try this :

      $ sudo apt-get install lame lame-extras

     Kellsens

---

### Post by Harkainos on 2007-07-08
That worked for the most part, Kell.

What about converting .WMA files over to MP3? This doesn't seem to do it.

Thank you.

---

### Post by kellsens on 2007-07-08
Take a look on this:

[http://ubuntuforums.org/showthread.php?t=37793](http://ubuntuforums.org/showthread.php?t=37793)

Kellsens

---

