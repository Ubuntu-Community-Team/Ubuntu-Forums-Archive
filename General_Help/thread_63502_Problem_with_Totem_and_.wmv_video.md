---
title: "Problem with Totem and .wmv video"
date: 2005-09-08
forum: General Help
---

### Post by feloc on 2005-09-08
I receive this while trying to play a video using Totem. What to do to get this video working. It's a windows media video.

"Video codec 'MSS2' is not handled. You might need to install additional plugins to be able to play some types of movies"

---

### Post by swamytk on 2005-09-08
Have you installed win32 codecs in your system?

# apt-get install w32codecs

The above command will do. But after updating this, I get video of wmv properly, but audio is jerking. I have installed latest w32codecs.

---

### Post by feloc on 2005-09-08
I had installed w32codecs, and it seems like some wmv videos work ok, some don't.

---

### Post by swamytk on 2005-09-08
I have heard about the mplayer, which handles wmv very well than any other player. Check the [http://www2.mplayerhq.hu/MPlayer/releases/codecs/essential-20050412.tar.bz2](http://www2.mplayerhq.hu/MPlayer/releases/codecs/essential-20050412.tar.bz2) for necessary decoders.

---

### Post by frodon on 2005-09-08
I have also sound problems with some .wmv files and totem but never with VLC player, you should try it  ;-) .

---

### Post by rafakl on 2005-09-08
Reading several forums, i get to the conclusion that Totem is the worst player.

All the people recommends to install other player and stop using totem.

Why dont you try "xine" ??? Its pretty and easy to use!!!

 \\:D/

---

### Post by frodon on 2005-09-08
First if you have installed totem-xine package what you have is xine with totem GUI, so install xine-ui or gxine will change nothing.
[QUOTE=rafakl]All the people recommends to install other player and stop using totem.
 \\:D/[/QUOTE]Not at all !!!!  , totem is one of the best players, really easy to use and install, the only common problem you could have with it is sound problem with .wmv. So for .wmv use VLC player and your problem is solved.
Mplayer is also one of the best players, but i find totem-xine easier to use and i also prefer the totem GUI than the mplayer's.

---

### Post by rafakl on 2005-09-08
i didnt knew that totem was only a GUI for xine!!! Thanks for the info.  ;-)

---

### Post by feloc on 2005-09-08
I got the video working with MPlayer. Thanks for the replies.

---

### Post by draven on 2007-06-25
vlc gives me the same error as totem:

[00000358] main decoder error: no suitable decoder module for fourcc `MSS2'.
VLC probably does not support this sound or video format.

---

### Post by freechelmi on 2008-01-09
> **draven said:**
> vlc gives me the same error as totem:

[00000358] main decoder error: no suitable decoder module for fourcc `MSS2'.
VLC probably does not support this sound or video format.

Hi I just Came accross this format with this video : 

[http://sw.nokia.com/id/105027dd-501a-4709-8c48-0da1d57bb0c0/VOIP_Webinar_27Nov06.wmv](http://sw.nokia.com/id/105027dd-501a-4709-8c48-0da1d57bb0c0/VOIP_Webinar_27Nov06.wmv)

It was recorded through Windows Live meeting and so the codec is Windows Media Screen 9 . Vlc does not handle it but it seems FFmpeg do so stay tune...

---

### Post by freechelmi on 2008-01-10
It's clear now that FFMPEG does not support those WMV variant right now , you have to use DMO , So Use pitfDLL for Gstreamer or mplayer or DMO module for VLC to play them : 

[http://wiki.videolan.org/Windows_Media_Video](http://wiki.videolan.org/Windows_Media_Video)

---

### Post by asezen on 2008-03-03
Hi guys,

I am having the same problem i am getting these error when i try to open a wmv;

[00000306] main decoder error: no suitable decoder module for fourcc `wmas'.
VLC probably does not support this sound or video format.
[00000354] main decoder error: no suitable decoder module for fourcc `MSS2'.
VLC probably does not support this sound or video format.

i read some tips on vlc wiki but nothing detailed, they said that we need to use dmo but how?

Could anybody explain how could we use vlc with dmo enabled?? 
I search google lots of way but no clean answer, you help will be appreciated, thx.

ps: video is cbt nuggets video...

---

