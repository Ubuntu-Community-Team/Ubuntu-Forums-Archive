---
title: "No Sound - Feisty.?"
date: 2007-08-29
forum: General Help
---

### Post by icehammer on 2007-08-29
Everything was ok till the morning - and i was listening to music..
As of now, i can't hear anything.. volume levels are ok, speaker is plugged in correctly, it works on the MP3 player.. but no sound if i connect it to Ubuntu..

I'm attaching a screenshot of the Vol Control. Lemme knw if u see something wrong..

Thanks..

---

### Post by aJayRoo on 2007-08-29
I'm sure you already tried but have a go at un-muting pc speaker and turn it up a bit see if that helps. If not then go to the terminal and type ```
alsamixer
```. This will launch the alsamixer console program, where you should have a play around with the levels and muting to try and get your sound back. If you succeed then exit alsamixer and save your settings with ```
sudo alsactl store 0
``` In my experience its always one level that is muted or too low, I don't know how it happens but I guess now and then it just does! If you are still stuck try [this](http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound) thread. Sorry that I can't be much more help than that!

EDIT: Also I have heard that updating your system can iron out this kind of sound loss, try: ```
sudo apt-get update
sudo apt-get dist-upgrade
```
if nothing else is successful (I can't vouch for the results of this as it is some one else's advice from a thread I read on here a while back).

---

### Post by bmorency on 2007-08-29
have you rebooted yet? I have had a similar problem before.  I am using KDE instead of gnome but the problem for me was i just hit ctrl-alt-backspace to restart the X server and KDE. it seems the KDE sound system just needed to be restarted.

---

