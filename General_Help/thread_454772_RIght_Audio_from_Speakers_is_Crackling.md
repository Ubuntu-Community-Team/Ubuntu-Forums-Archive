---
title: "RIght Audio from Speakers is Crackling"
date: 2007-05-25
forum: General Help
---

### Post by pianoboy3333 on 2007-05-25
As of recently I've noticed my **right audio is crackling**, in other words the audio from the right speaker when playing music. I tend not to think this is a physical hardware issue, but that is definitely a possibility. I can say that this **does not only pertain to gstreamer**, since it crackles in (in addition to **quod libet**) **totem** (which is using the xine engine) and **VLC**. If anyone could come up with some helpful suggestions on how to fix this, or how to isolate the issue, please let me know.

The song I have been using as a test is Good Times Bad Times by Led Zeppelin, this is an example of a bit that makes it crack (the beginning):

[http://www.geocities.com/pianoboy3333/gtbt.mp3](http://www.geocities.com/pianoboy3333/gtbt.mp3)
[http://www.geocities.com/pianoboy3333/gtbt_ogg.mp3](http://www.geocities.com/pianoboy3333/gtbt_ogg.mp3)

[SIZE="1"]Sorry about the unfortunate event that I had to put these up on geocities... my normal webserver is down... The one that is gtbt_ogg is an ogg file, geocities wanted the mp3 file name, so it is an ogg file, just with a .mp3 extension

(Interestingly enough, when creating the sound bit, it was not crackly in audacity but it was in all other programs)

I listen to the file in mp3 form, but I have attached an ogg file also for whatever the case.

By the end of writing this my audio was working fine again, but it didn't work after I rebooted...
[/SIZE]

---

### Post by mbradlcu on 2007-05-27
I've found that the pre drive can be set too high and overdrive the output stages. maybe this is your case. if so use the 'alsamixer' command and find the "Wave" virtual slider.. I set mine to about %50 and all is well.

---

