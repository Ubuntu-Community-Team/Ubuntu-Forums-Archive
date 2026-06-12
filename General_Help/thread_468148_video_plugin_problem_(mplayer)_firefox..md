---
title: "video plugin problem (mplayer?) firefox."
date: 2007-06-08
forum: General Help
---

### Post by bishop9226 on 2007-06-08
i switched my plugin from totem to mplayer and now i can watch video on cnn but i have no menu, it just shows the video.  the video wont play unless the website sets it to automatically start on its own (like cnn).  the video on cnn.com will play but again i have no fast forward/pause/play/stop controls.  videos that dont auto-start dont work at all and i have to download them

for example

[http://mediamatters.org/items/200706080002?f=h_latest](http://mediamatters.org/items/200706080002?f=h_latest)

and

[http://onegoodmove.org/1gm/1gmarchive/2007/06/republican_clus.html](http://onegoodmove.org/1gm/1gmarchive/2007/06/republican_clus.html)

say "(no video)" over a black screen but since there are no controls i cant start the video by clicking a play button.  

i tried

sudo apt-get remove mozilla mplayer

then

sudo apt-get totem-mozilla

but i dont think it did anything because im still using the same player.

how can i get mplayer to work or switch it to a better mozilla plugin embedded player?

thanks

---

### Post by bishop9226 on 2007-06-08
Help

---

### Post by cookies on 2007-06-08
Well, first, you can choose which plugins handle what in Edit > Preferences > Content > Manage

Next, try mousing over the bottom of the video window to see if the controls pop up. You may still be using Totem instead of MPlayer.

---

### Post by jimbob on 2007-06-08
If I fool around with it a bit like closing it, clearing cache and restarting I can get cnn.com videos most of which are WMV's to play using mplayer which is what starts up.

The interesting thing is when I go to edit->preferences->manage in FF it is set to "open with windows media player" ??  How can that be?  I don't have that on my system at all.  Should I change that to read mplayer instead?
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by sanguis on 2007-06-25
I am lost here as well, some one got and answer for us?

---

### Post by H.E. Pennypacker on 2007-06-25
CNN works just fine for me using mplayer-plugin (try checking out Preferences to see what's up), but if that doesn't work out, mozilla-mplayer, but there is also mozilla-plugin-vlc, which uses VLC, of course.

---

### Post by sanguis on 2007-06-26
> **H.E. Pennypacker said:**
> CNN works just fine for me using mplayer-plugin (try checking out Preferences to see what's up), but if that doesn't work out, mozilla-mplayer, but there is also mozilla-plugin-vlc, which uses VLC, of course.

ahhh dude, VLC is my standard.  thats great man.

---

