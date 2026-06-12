---
title: "mythtv: using an different (external) player in mythvideo"
date: 2014-02-07
forum: General Help
---

### Post by bric on 2014-02-07
mythtv 0.27 on Ubuntu 13.10

My video player of choice has come to be mplayer (mplayer2 actually).  I've learned all the (common) key shortcuts, and more importantly, taught everyone else in the house.

I installed Mythtv, let mythvideo download the covers/descriptions and it is a very nice looking front end for watching the video.

However, I can only get the internal player to work.  I've failed utterly to get mplayer to handle the video.

Help!  I've gone to settings > media > video  and then edited both 'filetypes' and 'player settings'.  I've entered:

mplayer
mplayer %s
mplayer -fs %s
/usr/bin/mplayer
/usr/bin/mplayer -fs %s 
etc..

and no luck.
When I go back to mythvideo and select a movie it doesn't do anything.  I need suggestions on what to do next to troubleshoot.

---

### Post by bric on 2014-02-09
I figured it out.  Finally... after entirely too many hours.

When you set up a directory in the backend this is called a 'storage directory'.  If you have done this then the path of the video sent to the player is myth://.... (or something).  Mplayer fizzles when it tries to play this.

So, start the backend configuration.  Find 'storage directories'.  Remove all the ones you feel like removing.  I was interested in mythvideo so removed the video storage group.  To remove a storage group press 'd'.  Exit from the backend.

In the frontend: directories are specified in 'settings > media settings > video settings > general'.  

'settings > media settings > video settings > player settings'
Set a default player (e.g., mplayer -fs %s).  

'settings > media settings > video settings > file types'
check the box for 'use default player'

Then go to videos, refresh the list ('m > scan for change' in mythvideo).  And finally, watch a video using mplayer.

hooray!

---

