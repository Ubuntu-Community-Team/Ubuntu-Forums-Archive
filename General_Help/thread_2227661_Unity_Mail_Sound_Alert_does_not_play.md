---
title: "Unity Mail Sound Alert does not play"
date: 2014-06-03
forum: General Help
---

### Post by Buschbarber on 2014-06-03
I have recently returned to Ubuntu since 14.04lts was released. I use Gmail and like receiving sound alerts when new mail arrives. I configured Unity Mail to check my Gmail account and notify me when new mail arrives. Under Options/Which application to execute on message receives, I chose usr/bin/aplay. Under Which custom sound to play, I chose my favorite wav file. No sound plays upon receipt of an email, but I do see a text notification.

If there is another app that will work properly to give me an audio alert when new messages are received in my Gmail Inbox, let me know.

---

### Post by grumblebum2 on 2014-06-03
The execute command doesn't seem to work here.
I tried to point to a script but nothing runs.
Command works in terminal though.
```
#!/bin/bash
/usr/bin/aplay /home/glen/Sounds/message.wav
```
I don't think the "execute command" is for defining what application plays the custom sound.
You would point it to open an email application or run a script.

I don't think you can change **what** plays the sound.
Wav or ogg files work here for a custom sound.
mp3's don't play.

It's using **canberra-gtk-play** here.
You can test your custom sound with...
```
canberra-gtk-play -f [COLOR="#808080"]*/path/to/soundfile*[/COLOR]
```

---

### Post by Buschbarber on 2014-06-04
Thanks! I was able to install gm-notify and add my sound file. I now receive a sound alert every time I receive an email in my Inbox.

---

