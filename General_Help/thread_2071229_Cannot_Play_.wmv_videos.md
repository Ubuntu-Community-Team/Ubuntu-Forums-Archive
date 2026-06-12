---
title: "Cannot Play .wmv videos"
date: 2012-10-14
forum: General Help
---

### Post by Robert R on 2012-10-14
HI, 

Does anyone know how to play .wmv  files, i have tried downloading and installing the following:

" GStreamer ffmpeg video plugin
Codecs to play mpeg, divx, mpeg4, ac3, wmv and asf files "

Alos tried using both VLC media player and movie player, in movie player the video does not show but i can hear the audio and in media player i get the following error:

"[COLOR=#ff0000]No suitable decoder module:[/COLOR]  [COLOR=#000000][COLOR=#000000]VLC does not support the audio or video format "MSS2". Unfortunately there is no way for you to fix this.[/COLOR]".
[/COLOR]

any help is greatly appreciated .

---

### Post by morbid_bean on 2012-10-14
Have you tried to install the **Ubuntu Restricted Extras**? 


I on the other hand am not able to play videos with that installed, but once I uninstall it, my videos work fine...  pretty odd...

---

### Post by Frogs Hair on 2012-10-14
I have no problem with Chrome but Firefox is choppy and I suspect the codec may not be fully supported in Firefox. I have not tried downloading any videos though.  
[http://vimeo.com/23172569](http://vimeo.com/23172569)

---

### Post by mc4man on 2012-10-15
mss2 (microsoft screen codec - Windows Media Video 9 Screen) can only be decoded in a 32bit mplayer with w32codecs installed.

---

### Post by Robert R on 2012-10-15
> mss2 (microsoft screen codec - Windows Media Video 9 Screen) can only be decoded in a 32bit mplayer with w32codecs installed.


Does this mean that Ubuntu cannot play .wmv videos ? 

If no where can i get this codec.

---

### Post by mc4man on 2012-10-15
> **Robert R said:**
> Does this mean that Ubuntu cannot play .wmv videos ? 

If no where can i get this codec.
No, it means that only mplayer on a 32 bit install with w32codecs can decoded a wmv that is mss2 format
(wmv is just the container
All the other varieties of wmv will work just fine with most players
(wmv2, wmv3, Vc-1, ect.

If you are on a 32 bit install then install mplayer, a frontend if desired like smplayer, gnome-mplayer, kplayer, umplayer, ect.

You can get 32codecs from here
[http://packages.medibuntu.org/precise/w32codecs.html](http://packages.medibuntu.org/precise/w32codecs.html)
(just download & d. click on the .deb to install

---

