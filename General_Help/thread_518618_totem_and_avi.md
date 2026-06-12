---
title: "totem and avi"
date: 2007-08-06
forum: General Help
---

### Post by ali780 on 2007-08-06
Hi
My totem player can not play avi files. How can I fix it?
Thanks

---

### Post by ali780 on 2007-08-06
I should add that this problem is with divx and xvid files

---

### Post by Hallvor on 2007-08-06
Have you tried

> sudo apt-get install w32codecs

and 

> sudo apt-get install libxine-extracodecs gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-pitfdll

?

---

### Post by ali780 on 2007-08-06
:lolflag:

---

### Post by robmcknz on 2007-08-06
I tried both of those and my totem player still says "There is no plugin to handle this movie.":mad:

---

### Post by por100pre1 on 2007-08-06
Check at [www.medibuntu.org]("http://www.medibuntu.org")...

---

### Post by ali780 on 2007-08-06
I tried both of them and the problem is fixed now
:guitar:

---

### Post by bruckwine on 2007-08-06
Speaking of which I notice my totem TRIES to play video..you get the 1st sec or two then a black screen - somethign witht he rendering I figure but  haven't figured out how to change that yet.

---

### Post by Hallvor on 2007-08-06
If you can`t make the codecs work, try VLC. It uses its own codecs and should play anything but realmedia files.

---

### Post by Gremlinzzz on 2007-08-06
smplayer package (Qt3; without KDE support
[http://wesley.debianbox.be/packages/](http://wesley.debianbox.be/packages/)
Use mplayer plugin and put these commands in terminal
cd /usr/lib/firefox/plugins/
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.xpt
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.s
:guitar:

---

### Post by protokaiser on 2007-08-06
> **Gremlinzzz said:**
> smplayer package (Qt3; without KDE support
[http://wesley.debianbox.be/packages/](http://wesley.debianbox.be/packages/)
Use mplayer plugin and put these commands in terminal
cd /usr/lib/firefox/plugins/
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.xpt
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.s
:guitar:

Yeah I did this and the video and audio work, but they're not synched. I don't think it's the file, cus it's works fine on my desktop which is running windows. Any ideas?

---

