---
title: "AACplus online radios?"
date: 2005-07-25
forum: General Help
---

### Post by kblood on 2005-07-25
Hello everyone,

Recent Ubuntu convert, long-time Windows user, I am in the process of migrating to Ubuntu for good, and feeling quite happy so far!

Now, a silly question: I like listening to online radios from this list:
[Tuner2](http://www.tuner2.com)
These have a really nice quality for a very low bitrate, using AAC+, or AACplus, as you prefer... (I like [Radio Paradise](http://www.radioparadise.com) :) )

However, I have faad installed, I ran the gstreamer configuration program, and I see that the faad plugin is installed, so everything seems to be ok...
But Rhythmbox and XMMS refuse to play the stream!
I can play it with VLC 0.8.1, but it plays in 22050Hz, which sounds quite crappy compared to the truly beautiful sound of 44100Hz that I get with Winamp in Windows.

Has anybody succeeded in playing AACplus streaming online radios in full quality?

If not, I am considering going the Wine way, and trying Foobar and/or Winamp... Any experience with this?

Looking forward to your tips!!! Thanks in advance!

---

### Post by diffuser78 on 2005-07-25
[QUOTE=kblood]Hello everyone,

Recent Ubuntu convert, long-time Windows user, I am in the process of migrating to Ubuntu for good, and feeling quite happy so far!

Now, a silly question: I like listening to online radios from this list:
[Tuner2](http://www.tuner2.com)
These have a really nice quality for a very low bitrate, using AAC+, or AACplus, as you prefer... (I like [Radio Paradise](http://www.radioparadise.com) :) )

However, I have faad installed, I ran the gstreamer configuration program, and I see that the faad plugin is installed, so everything seems to be ok...
But Rhythmbox and XMMS refuse to play the stream!
I can play it with VLC 0.8.1, but it plays in 22050Hz, which sounds quite crappy compared to the truly beautiful sound of 44100Hz that I get with Winamp in Windows.

Has anybody succeeded in playing AACplus streaming online radios in full quality?

If not, I am considering going the Wine way, and trying Foobar and/or Winamp... Any experience with this?

Looking forward to your tips!!! Thanks in advance![/QUOTE]


Try gxine

sudo apt-get install gxine


I hope it should work!!!!

---

### Post by kblood on 2005-07-25
I tried already with Gmplayer and with Xine-ui, and no luck. I believe they use the same libraries...

But I will give it a try!

Have you tried it?

---

### Post by kblood on 2005-08-09
Well, no luck so far... I have been surviving on other options for online listening, found a couple of nice Ogg streams.

Still it's quite frustrating, I have tried Totem-xine, Gmplayer, Rhythmbox, XMMS, Beep Media Player, Somaplayer, Real Player 10... None of these can do anything with this aac+ (aacplus) stream.

VLC plays the stream, but doesn't detect the aac+ part, and plays it in 22050Hz... and that's very easy to notice...

Anybody has any ideas?

This is for online radios like [www.sky.fm](www.sky.fm), [www.di.fm](www.di.fm), [www.radioparadise.com](www.radioparadise.com), and all the ones found in [www.tuner2.com](www.tuner2.com)... They sound really nice, considering the bitrate!

---

### Post by sean_malice on 2005-12-10
I have the same problem. 
However, my version of vlc plays the SBR "+" part just fine at 44Khz. Try upgrading or reinstalling maybe. You can be sure of the right decoding by stopping and playing the stream several times. At some point, you hear the 22KHz stream and the 44KHz part kicking in soon after.  Here's my version number :

VLC media player 0.8.4-svn20040920 Janus
VLC version 0.8.4-svn20040920 Janus
Compiled by [email]buildd@terranova.buil[/email]dd
Compiler: gcc version 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)

no fancy visualisation with vlc however :( 

Hope this helps

---

