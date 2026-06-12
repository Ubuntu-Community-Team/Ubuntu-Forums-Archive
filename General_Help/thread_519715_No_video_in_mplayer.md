---
title: "No video in mplayer"
date: 2007-08-07
forum: General Help
---

### Post by andyrobo60 on 2007-08-07
Until a few days ago mplayer was working fine. Now when ever I try to open a video in mplayer with the GUI the window with the video in closes before mplayer can start playing. Leaving me with only the sound. However if I open a video in mplayer from the terminal without using the GUI it works fine. If I use gmplayer to open the video then I get no video again. 

Has anyone had this problem before or know of anything that maybe able to fix it.

---

### Post by tbroderick on 2007-08-08
Are there any error messages when you type in gmplayer from a terminal?

---

### Post by tprotocol on 2007-11-22
Same thing happened to me after I enabled an over-the-wire update of mplayer.

The update changed my /root/.mplayer/gui.conf file.

BEFORE UPDATE:
vo_driver = "xv"

AFTER UPDATE:
vo_driver = "null"

So I changed it back and restarted gmplayer, and gmplayer displayed video and played audio as normal before the update.

---

