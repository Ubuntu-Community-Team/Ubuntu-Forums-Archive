---
title: "cnn video doesn't work anymore (dapper)"
date: 2007-02-26
forum: General Help
---

### Post by steve196 on 2007-02-26
[www.cnn.com](www.cnn.com) video always worked with firefox+mplayer. The last few days it stopped working (without me changing any configuration). It tries to buffer something but the progress bar shows no progress. It gets stuck alternately trying to connect to two different ip adresses. Other sites that have video still work fine. Also on win2k (firefox, wmp, same machine) the problem doesn't exist.

---

### Post by steve196 on 2007-02-27
Solved by unchecking "play media directly from site". No idea why.

---

### Post by _axiom_ on 2007-04-13
I have the exact same problem on KDE.  I use Firefox, but I had them playing though Kaffeine, and now all I get is that buffering thing+wierd visualizations of nothing.

Is their an analogous option in kaffeine, or do I need to switch to totem or something?

Just for kicks, I tried it in konqueror, and one video actually worked in CNN's little player interface (never seen that before always had to hack around it), but then I couldn't get any more to play.

---

### Post by ronocdh on 2007-04-21
> **_axiom_ said:**
> I have the exact same problem on KDE.  I use Firefox, but I had them playing though Kaffeine, and now all I get is that buffering thing+wierd visualizations of nothing.

Is their an analogous option in kaffeine, or do I need to switch to totem or something?

Just for kicks, I tried it in konqueror, and one video actually worked in CNN's little player interface (never seen that before always had to hack around it), but then I couldn't get any more to play.
I fortuitously came across the solution by using one of Kilz's scripts from the 64-bit forum. To mimic the effect, go to Synaptic and search for "mozilla-plugin." Remove all packages that might be playing video in Firefox (VLC, etc.). Then search for "mplayer" and add it, as well as the mplayer browser plugin. Boom, fixed.

Kudos to Kilz.

---

### Post by pkeegan on 2007-04-22
> **steve196 said:**
> Solved by unchecking "play media directly from site". No idea why.Where exactly is this setting?
Thanks

---

### Post by Dayylin on 2007-04-25
> **pkeegan said:**
> Where exactly is this setting?
Thanks

For [www.cnn.com](www.cnn.com), once the video pops up, right click on the video and then on configure. You can then uncheck the 'play video from site'

---

### Post by mindracer on 2008-05-28
I have Hardy 8.04 and CNN Live video doesnt work.  They require you to install a plugin in Windows and maybe MAC.

Please use this form to let them know you miss CNN Live Video on Ubuntu/Linux:

[http://www.cnn.com/feedback/forms/form9d.html](http://www.cnn.com/feedback/forms/form9d.html)


If you have found a workaround, please let us know..

---

### Post by nooblot on 2008-07-04
aww f**k CNN...doesn't work for me either.....

[my plugins]("http://farm4.static.flickr.com/3148/2637335567_d77540df7e_b.jpg")

---

### Post by Turkten on 2008-07-10
Well, you can't view it in your browser but... I have a way to watch it. As far as media players go, I prefer VLC. This may or may not work with others. I have not tested it. I am using 8.04.

Here's my steps..

1) Open Terminal
2) sudo apt-get install vlc
3) run vlc
4) File -> Open Network Stream
5) In the HTTP/HTTPS/FTP/MMS field, put in the following address:

[http://www.cnn.com/video/live/cnnlive_1.asx](http://www.cnn.com/video/live/cnnlive_1.asx)

This worked for me and, once it starts playing, if you go into View -> Playlist, you can click Manage -> Save Playlist. I just save it as CNN Live Stream and then it's always there.

---

