---
title: "strange (unique?) nforce2 alsa xine problem"
date: 2005-10-22
forum: General Help
---

### Post by claymore on 2005-10-22
Well, after a break to try a few other distros, I am back in Ubuntu and loving it, except for one bizarre problem.

When I'm using alsa in xine, everything works like a charm, until I try to change audio streams.  Then I get an error that the audio device is already in use.  It happens on most (but not all) DVDs, and I have never had this problem in other distributions.  I'm not sure whether it's a problem with xine, gstreamer, alsa or the libdvdcss decoder.  Now, I am able to play multiple sound streams with the sink set to alsa at the desktop, so I know that's not the problem.  Is there a way to have Ubuntu only play one sound stream at a time like other distros?  I wonder if that might solve my problem.

I have followed several of the Ubuntu multimedia howtos and tried several /etc/esound/esd.conf and ~.asoundrc versions to try and solve the problem, and all they have done is degraded my sound quality or changed nothing.

I use 5.1 analog from my nforce2 board with alsa.  I can't replicate the error with mplayer or vlc.  mplayer works fine but won't play DTS tracks, and I can't seem to get the channels right in 5.1 mode in vlc (the center and rear left channels are reversed for some reason)

If anyone would have suggestions to either get xine to switch streams properly and/or get vlc to play 5.1 with the right channels, it would be greatly appreciated.

-thanks

---

