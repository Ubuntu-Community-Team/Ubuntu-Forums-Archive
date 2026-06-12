---
title: "Problem with Audacity"
date: 2005-06-24
forum: General Help
---

### Post by frank_y on 2005-06-24
I installed all of the codecs and the lame library, and playing mp3 files iwth totem and etc works. However, when I try to edit audio files with audacity, it says "there was an error initializing the audio i/o layer, you will not be able to play or record audio." I opened a few audio files to test, and mp3's showed up fine (but didnt play) and when I tried opening a locally recorded ogg, it showed up blank. Does anyone have any idea what is wrong?

---

### Post by Xian on 2005-06-24
[QUOTE=frank_y]However, when I try to edit audio files with audacity, it says "there was an error initializing the audio i/o layer, you will not be able to play or record audio." [/QUOTE]
This generally indicates a sound server conflict. 
To verify, shut down esd (or arts if in KDE) and try to use Audacity again.

---

### Post by Karlos on 2005-06-24
take a look at these threads when you get a chance

[http://www.ubuntuforums.org/showthread.php?t=26567&highlight=sound](http://www.ubuntuforums.org/showthread.php?t=26567&highlight=sound)

[http://www.ubuntuforums.org/showthread.php?t=32063&highlight=sound](http://www.ubuntuforums.org/showthread.php?t=32063&highlight=sound)

I found them very helpful

---

