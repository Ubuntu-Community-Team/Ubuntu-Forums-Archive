---
title: "firefox and quicktime streaming"
date: 2005-07-15
forum: General Help
---

### Post by jmleonfounlin on 2005-07-15
Hi,

I have a network made up of a G5 with Max O X 10.4.2 and a laptop with Ubuntu Hoary. I am experimenting with video streaming from the Mac to the Linux box locally (not across the internet). Apple's Web Sharing serves my local web pages to my linux notebook. And I use Apple's free QT Broadcaster to stream some video from my iSight in manual unicast mode. The reference movie exported from QT Broadcaster is in .mov format (embedded in a page on my website) and I used the default H.264 codec (though I've tried other codecs too). I've got mozilla-vlc and mplayer plugins installed on the Ubuntu side.

I  have tested a local loop, that is streaming from my mac to itself and it works. I can see the streaming embedded in a webpage on my local web server. On linux with Firefox 1.0.4 I've got the page of the streaming but no video. Apparently the default plugin is mplayer (version 2.70). It says it is transferring data but no video is showing not even my poster frame (a nice picture of me, too bad!). So apparently the plugin doesn't handle the qt streaming very well. I can view qt movies on Apple's QT page (Dido's DVD extract e.g.) however.

I have uninstalled mplayer plugin to have firefox use another one but it crashes if I try I to access my video page without the mplayer plugin. so I had to reinstall it.

How do I tell Firefox to use another plugin or how do I make the mplayer plugin work with streaming .mov files?
What codec is more appropriate (H.264, H.263 and so forth)?
What am I doing wrong?

Thanks in advance for your replies and help.

---

### Post by arnieboy on 2005-07-15
this is how to do it: u need to install the latest version of mplayerplug-in and also install the codecs.
[http://ubuntuforums.org/showthread.php?t=44560](http://ubuntuforums.org/showthread.php?t=44560)

---

