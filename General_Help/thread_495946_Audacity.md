---
title: "Audacity"
date: 2007-07-08
forum: General Help
---

### Post by liquidfunk on 2007-07-08
When I open up Audacity, I get the following error:

 ¨There was an error initializing the audio i/o layer. You will not be able to play or record audio.

 Error: Host error.¨

 Help!

---

### Post by ronocdh on 2007-07-10
How well supported is your soundcard? You can find this out on the ALSA mainpage; there's a listing for pretty much every audio card under the sun. Also, how does Ubuntu react when you open other programs with audio recording capability? I would try messing around in the Sound preference panel and seeing whether you can't get a workable setup to record.

---

### Post by dabl on 2007-07-10
Make sure you've got all the alsa and oss packages that seem to be appropriate.  Then, if you get past the "error opening audio I/O" thing, open your "Volume Control" aka Mixer, and fiddle with the "Edit">"Preferences" as ronocdh suggested.

---

