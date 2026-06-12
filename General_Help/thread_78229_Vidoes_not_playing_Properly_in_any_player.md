---
title: "Vidoes not playing Properly in any player"
date: 2005-10-18
forum: General Help
---

### Post by geekydiv on 2005-10-18
I had a hoary install on my system earlier and installed all the video codecs specified in ubuntuguide.org and my video's worked fine in xine.
Now i have reinstalled breezy on the same system. But now when i install all the codecs 
gstreamer0.8-plugins
gstreamer0.8-lame
gstreamer0.8-ffmpeg
w32codecs ( got it from a link on the net)
lame
sox
ffmpeg
mjpegtools
vorbis-tools
libdvdcss2 (another link on the net)

along with xine-ui, i have a problem of frames dropping. The only codec i could not find in breezy was libdivx4linux. 

Then i installed mplayer. The video is playing fine in window screen but when i do a full screen i get the same size as the window & not the full screen. I get a black border all around in full screen mode surrounding the border. 

Then i installed totem-xine , gxine & vlc - All the three play the videos well  in window mode but in full screen mode i dont get the smoothness i should get. I see a lot of frame cuts as if its jumping. 

I would be really grateful if soemone can help me solve this problem which has cropped up in breezy where as it was not present in hoary.

---

### Post by Jurgen272 on 2005-10-18
DMA is probably not active on the DVD-drive.

---

### Post by geekydiv on 2005-10-18
I am trying to play the videos of my harddisk like avi,mpeg & wmv. I did try to play a dvd also with the same result. I just saw the tutorial on how to enable dma in ubuntu wiki but did not understand properly wat to do as it has been given with a warning. Wat is suggested to be done.

---

### Post by maqi on 2005-10-18
I find xfmedia to be the best media player for linux. It does not have any bells and whistles but it plays well. i found totem to be a complete waste of time whether with g-streamer (which I no longer use) or xine. I experienced exactly the same symptoms you're describing. 

Mplayer seems to be sort of OK, but it's just so UGLY.

Anyways to cut a long rant short ;) I can highly recommend xfmedia as a media player. It plays more formats reliably than any of the others I've tried. 

It doesn't have a media library, but it does have play lists. All you need to do is stick all of your media files under one or two (or three) directories and then add those directories to the play list. Yuo can save that playlist as your "media library". However, you will have to manually update your playlists.

Hope this helps :)

---

### Post by geekydiv on 2005-10-18
I have installed xfmedia. It palys audio well but video, i dont get anythin. The player just hangs up. is it needed to be configured. Please help

---

### Post by maqi on 2005-10-19
Hey geekydiv,

That's weird. Xfmedia was the first player that "just worked" for me. Provided that you have the relevant codecs installed for xine or g-streamer (whichever you use) it should work.

It sounds like your problem is at a deeper level than the player. You may need to check your multimedia configs. 

Sorry I can't be more help :(

---

