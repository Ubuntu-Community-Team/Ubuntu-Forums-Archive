---
title: "Flash Sound and Video"
date: 2006-07-03
forum: General Help
---

### Post by uab999 on 2006-07-03
I have installed the flash player (Macromedia) plugin for firefox.  However, it seems that I cannot watch flash video.  For example, youtube.com: The videos load and start to play, but they only play for 2 seconds and then stop.  There is no sound during the videos at all.  When I try to listen to music, there is no sound as well.  For example, at pandora.com.  It uses flash audio, but I get no sound.  I'm wondering if anyone else has had this problem, and if it can be fixed.  Thanks.

I use Ubuntu 6.06 and firefox.

---

### Post by jakez on 2006-07-03
It works for me, i did:
sudo apt-get install flashplugin-nonfree
sudo update-flashplugin
and restarted firefox
Hope it helps

---

### Post by uab999 on 2006-07-03
Yeah, I've done that before.  The flash player works; it shows flash animation like games and stuff.  However, the videos will not play.  Every time I try to play a video, it goes for two seconds and stops.  Then, when I try to close firefox or go to another website, it freezes and I have to force quit.

---

### Post by Rui Pais on 2006-07-03
Hi,
mind to try my suggestion on [this thread]("http://ubuntuforums.org/showthread.php?p=1186640#post1186640")? 
If it still fails give a look at the solution/workaround pointed in this [bug report]("https://launchpad.net/distros/ubuntu/+source/flashplugin-nonfree/+bug/29760") (the comment of D. Carrera)

hope that helps

---

### Post by uab999 on 2006-07-03
Thanks a lot Rui Pais!  That finally fixed it!

---

### Post by Rui Pais on 2006-07-03
No prob. 

I have a link on my bookmarks to that thread since i found so many people asking for that specific issue... ;)

Have fun.

---

