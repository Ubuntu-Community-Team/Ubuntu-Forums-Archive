---
title: "No video sound in Breezy with Totem"
date: 2005-10-21
forum: General Help
---

### Post by harnadem on 2005-10-21
:(  I am running Breezy on a computer using a C-Media PCI audio card, and am using ALSA.  The desktop sounds work, and Rhythmbox plays my CD's fine.  However, when I run an .mpg file using totem there is no sound, but the video plays okay.  Is there a fix for this?

---

### Post by arunsub on 2005-10-21
Did you install gstreamer and other plugins. Did you try sound how-tos like [http://www.ubuntuforums.org/showthread.php?t=26567](http://www.ubuntuforums.org/showthread.php?t=26567) ? If so, then try using another player like VLC. Sound doesn't work for me for some mpg and wmv files in totem and i use VLC for those clips. It works fine.

---

### Post by moopere on 2005-10-21
[QUOTE=arunsub]Did you install gstreamer and other plugins. Did you try sound how-tos like [http://www.ubuntuforums.org/showthread.php?t=26567](http://www.ubuntuforums.org/showthread.php?t=26567) ? If so, then try using another player like VLC. Sound doesn't work for me for some mpg and wmv files in totem and i use VLC for those clips. It works fine.[/QUOTE]

I have found with all versions of Totem (gstreamer versio) so far that they are broken.  A quick change to totem-xine usually fixes everything and 'just works' - I don't really understand why xine is not the default.

Cheers,
Craig

---

### Post by harnadem on 2005-10-21
[QUOTE=moopere]I have found with all versions of Totem (gstreamer versio) so far that they are broken.  A quick change to totem-xine usually fixes everything and 'just works' - I don't really understand why xine is not the default.

Cheers,
Craig[/QUOTE]

I should have clarified.  I am running Totem-xine (and not gstreamer).  I will try the sound how-to and see what happens.

---

### Post by harnadem on 2005-10-26
Still no luck trying to get the audio working when using Totem-xine.  Seems to work fine for other applications except Totem.  Any ideas of what to do to fix it?

---

### Post by audax321 on 2005-10-26
I had a similar problem. Try this: [http://www.ubuntuforums.org/showthread.php?t=80299](http://www.ubuntuforums.org/showthread.php?t=80299)

But, I have to warn you that my sound is messed up now. If I play an mp3 file the bass is horrible. But sound works with video. I'm probably going to try a clean install when I get the chance and see if I can find out what is going wrong. Did you install the w32codecs and libdvdcss2 and where did you install them from. I had them installed from 

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) sarge main

but then came across this repo:

deb [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) breezy main

which actually has breezy versions of the packages.

---

### Post by harnadem on 2005-10-27
:D  Audax321, thanks for your reply.  I am running the latest Breezy.  The good news is that I managed to fix the audio in Totem.  What I did was install both, vlc and the vlc-plugin-alsa.  Now, I am able to play video using vlc.  Also, the audio now works in Totem-xine (don't ask me why, I don't know).  Now if I can just get my palm to sync with Evolution I would be 100 percent linux.

---

### Post by Breezy Badger on 2005-10-27
I must also say that I had this exact same problem and It was fixed by getting the above vlc plugins, just do that and you totem sound will work.

thanks so much guys

Badger

---

### Post by audax321 on 2005-10-28
:(  Installing those VLC packages did nothing for me. Oh well, I'm going to reinstall and next time I run into that problem I'll install those VLC packages instead of reinstalling gstreamer plugins. Ubuntu better fix these problems, it probably doesn't speak to much in favor of this distribution if they break things that worked in previous releases. Sound, however, appears to be a problem in many distros.

---

### Post by ziad on 2006-01-28
had the same problem as you and this solved it:

[http://www.ubuntuforums.org/showthread.php?t=69839&highlight=sound+wmv](http://www.ubuntuforums.org/showthread.php?t=69839&highlight=sound+wmv)

hope I am not too late. totem-xine works great by the way.

[QUOTE=audax321]:(  Installing those VLC packages did nothing for me. Oh well, I'm going to reinstall and next time I run into that problem I'll install those VLC packages instead of reinstalling gstreamer plugins. Ubuntu better fix these problems, it probably doesn't speak to much in favor of this distribution if they break things that worked in previous releases. Sound, however, appears to be a problem in many distros.[/QUOTE]

---

