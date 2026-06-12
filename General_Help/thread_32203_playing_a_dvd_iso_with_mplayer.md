---
title: "playing a dvd iso with mplayer"
date: 2005-05-06
forum: General Help
---

### Post by logan2004 on 2005-05-06
hello all
im trying to play a dvd iso file with mplayer. from what i understand, i should mount the file to /media/dvd then i should be able to open it like a normal dvd in mplayer

here's the command i used to mount the file:

```
sudo mount -o loop ahx.iso /media/dvd
```

when i start up mplayer and try to play the dvd i get the error "Can't open VMG info!"

any help would be much appreciated!

thanks,
logan

---

### Post by Leif on 2005-05-06
I don't know about mplayer, but you might want to try out VLC. I have yet to see a format it's failed to open.

---

### Post by logan2004 on 2005-05-06
thanks! im trying out the package gnome-vlc right now, ill let you know if it works.

---

### Post by logan2004 on 2005-05-06
the video works fantastic!!! but i get no audio whatsoever... any ideas??

---

### Post by Leif on 2005-05-06
Not too sure. I'm guessing your audio works with other programs. Check what your audio settings are (preferences->multimedia systems selector). Mine are ESD / OSS source/sink. Make sure VLC is using the same, although with me it worked out of the box.

Finally, just check whether you have the audio problem with other files, try opening a simpler avi, or mp3 with VLC.

---

### Post by logan2004 on 2005-05-07
hmm, i dont seem to be getting any audio from vlc whatsoever..

any ideas?

---

### Post by bored2k on 2005-05-07
[QUOTE=logan2004]hmm, i dont seem to be getting any audio from vlc whatsoever..

any ideas?[/QUOTE]
 ```
sudo apt-get install vlc-esd
```
Then settings > preferences > audio > advanced options [CHECK] > audio output module > EsounD

---

### Post by logan2004 on 2005-05-07
thanks! ut i just got the audio to work by going to system > preferences > sound and unchecking "enable sound server startup"

can anyone tell me why this works when that is unchecked?

---

### Post by bored2k on 2005-05-07
[QUOTE=logan2004]thanks! ut i just got the audio to work by going to system > preferences > sound and unchecking "enable sound server startup"

can anyone tell me why this works when that is unchecked?[/QUOTE]
 VLC is probably using the wrong audio output module. You shouldn't have to do that. I suggest you follow Gandalf's [http://ubuntuforums.org/showthread.php?t=32063&highlight=alsa+esd](http://ubuntuforums.org/showthread.php?t=32063&highlight=alsa+esd) and install vlc-alsa.

---

### Post by logan2004 on 2005-05-07
thanks!!!!!!!!

---

