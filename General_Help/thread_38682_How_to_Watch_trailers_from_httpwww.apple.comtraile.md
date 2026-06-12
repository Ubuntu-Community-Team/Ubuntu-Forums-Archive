---
title: "How to Watch trailers from http://www.apple.com/trailers/  in Ubuntu?"
date: 2005-06-01
forum: General Help
---

### Post by galactus51 on 2005-06-01
Hi folks!! I'm trying to watch trailers from [http://www.apple.com/trailers/](http://www.apple.com/trailers/) . I am using  the Mplayer Plug-in in FireFox. It starts to download the archive and seconds later the download stops   or FireFox freeze . What can I do to solve the problem? There is anyway to watch this trailers with another plug-in, like's xine? 
By the way, win32codecs are already installed, but  libavcodecs and libc6 "libraries" are not installed, because Ubuntu Repositories don't have it.
 
Sorry, about my poor English.

Thanks for any help!

---

### Post by derrick1985 on 2005-06-01
[QUOTE=galactus51]Hi folks!! I'm trying to watch trailers from [http://www.apple.com/trailers/](http://www.apple.com/trailers/) . I am using  the Mplayer Plug-in in FireFox. It starts to download the archive and seconds later the download stops   or FireFox freeze . What can I do to solve the problem? There is anyway to watch this trailers with another plug-in, like's xine? 
By the way, win32codecs are already installed, but  libavcodecs and libc6 "libraries" are not installed, because Ubuntu Repositories don't have it.
 
Sorry, about my poor English.

Thanks for any help![/QUOTE]


Here is how I FINALLY got everything to work properly.

Follow the multimedia guide located [http://www.ubuntuguide.org/#codecs](http://www.ubuntuguide.org/#codecs)
Install RealPlayer [http://www.ubuntuguide.org/#realplayer](http://www.ubuntuguide.org/#realplayer)
Follow the Howto to hear multiple sounds (this way, real player will work without having to kill esd) [http://ubuntuforums.org/showthread.php?t=32063](http://ubuntuforums.org/showthread.php?t=32063)
Install xine-ui [http://www.ubuntuguide.org/#xine-ui](http://www.ubuntuguide.org/#xine-ui)

Install the MediaPlayerConnectivity plug-in for Firefox
[https://addons.mozilla.org/extensions/moreinfo.php?id=446](https://addons.mozilla.org/extensions/moreinfo.php?id=446)

Run the Configuration Wizard. Set the Video player for Quicktime to xine-ui (it should detect it) Set RealPlayer to realplay, Windows Media to xine-ui, and finally, your choice for music (mine's xmms for streaming)

The next two settings are up to your, wether or not you want the streams to open up in your desired media players, i choose no, personally, but it's up to you.

Enjoy.

---

### Post by galactus51 on 2005-06-01
Thanks a lot!!!!!!!!!! It works!!!!!!!!!! Finally!!!!!!!
But just one thing, I did not find:
"Run the Configuration Wizard. Set the Video player for Quicktime to xine-ui (it should detect it) Set RealPlayer to realplay, Windows Media to xine-ui, and finally, your choice for music (mine's xmms for streaming)

The next two settings are up to your, wether or not you want the streams to open up in your desired media players, i choose no, personally, but it's up to you."

But it have worked. Another thing, after restart the system, the Multimidia configuration returns to OSS sound, I have tryed to change both to ALSA, but I got a error message when testing the "font" . I've changed anyway and worked.

That's it. Thanks very much again!!!!!!!!!!!

---

### Post by derrick1985 on 2005-06-02
[QUOTE=galactus51]Thanks a lot!!!!!!!!!! It works!!!!!!!!!! Finally!!!!!!!
But just one thing, I did not find:
"Run the Configuration Wizard. Set the Video player for Quicktime to xine-ui (it should detect it) Set RealPlayer to realplay, Windows Media to xine-ui, and finally, your choice for music (mine's xmms for streaming)

The next two settings are up to your, wether or not you want the streams to open up in your desired media players, i choose no, personally, but it's up to you."

But it have worked. Another thing, after restart the system, the Multimidia configuration returns to OSS sound, I have tryed to change both to ALSA, but I got a error message when testing the "font" . I've changed anyway and worked.

That's it. Thanks very much again!!!!!!!!!!![/QUOTE]

No problem, glad to hear it worked for you.

When you restart firefox, mediaplayerconnectivity should have run you through a wizard, searching out your video players and letting you select the ones you want to use.

As for your sound issue of your machine changing back to OSS, that i'm not sure on. If it becomes a problem, post in the thread I gave you a link to set it up wiht.

---

### Post by galactus51 on 2005-06-02
Hi, dispite the error message with ALSA sound, it is working fine and did not return to OSS anymore. Well, when I restarted FireFox, mediaplayerconnectivity did not run any wizard but again, everything is working fine.

With your permission I'll write this tutorial in Brazilian - Portuguese, and sure I will put your name and the other guys that wrote the tutorial. 

Thanks again!!!

---

