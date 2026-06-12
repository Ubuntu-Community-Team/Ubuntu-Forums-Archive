---
title: "video playback, info"
date: 2007-08-28
forum: General Help
---

### Post by hallbrian on 2007-08-28
Am having some trouble with playing movies, which all work fine, till i have desktop effects/beryl running the movies play fine but dont get a picture i have to move the window around a bit till the picture comes up, also full screen does not work.

Could this be because am not running my beryl in a xgl session, my desktop effects all work fine without running an xgl session, was wondering if this may be the problem am having..

Cheers
Brian

---

### Post by raijinsetsu on 2007-08-28
It sounds like your media player is using overlays... You might try changing the renderer it's using.

---

### Post by hallbrian on 2007-08-28
Thanks for the quick reply but dont think it would be that, as it works fine, even get full screen before i enable any desktop effects/beryl.

Its only after am running berly (which is running with no problems) that i have to move the window around to see the video.

Cheers
Brian

---

### Post by raijinsetsu on 2007-08-28
Right... Beryl uses your video card to render to the screen. If you're using a renderer in your media player that is attempting to do the same thing(ie. direct rendering), then you will sometimes get artifacts like this.
What media player are you using?

---

### Post by hallbrian on 2007-08-28
The standard player that comes with ubuntu, not sure what it is, the menu just says movie player.

This is not a big problem for me, just one click and i can disable berly to play a movie, but would  be nice to have it working. 

Cheers
Brian

---

### Post by raijinsetsu on 2007-08-28
Go into the media players preferences and see if you can use a different renderer. That should solve your problem.

---

### Post by hallbrian on 2007-08-28
no cant see anything to do with rendering, tryed using vlc but that will not play anything over the network it has to be coped first before i can play anything.

Cheers
Brian

---

