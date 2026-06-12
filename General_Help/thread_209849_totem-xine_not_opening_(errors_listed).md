---
title: "totem-xine not opening (errors listed)"
date: 2006-07-05
forum: General Help
---

### Post by blackjack6.21.91 on 2006-07-05
When I try to launch totem-xine, it appears for just a bit and then disappears.  When launching in a terminal ([COLOR="Blue"]# totem[/COLOR]), the following error appears.  This did not happen in totem-gstreamer.

> [COLOR="Blue"]#totem[/COLOR]
[COLOR="Red"]The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 69 error_code 11 request_code 141 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)[/COLOR]


Note: when I do [COLOR="Blue"]#totem --sync[/COLOR] the same error appears.

---

### Post by blackjack6.21.91 on 2006-07-06
Alright.  For anyone who has this problem, it turns out there is a bug in totem-xine.  It is described [here]("https://launchpad.net/distros/ubuntu/+source/totem/+bug/35229").
Some suggest installing totem-gstreamer with the following packages, but that does not offer subtitle support.

gstreamer0.10-ffmpeg
gstreamer0.10-pitfdll
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse
totem-gstreamer-firefox-plugin

---

### Post by GoodPanos on 2006-07-06
May I make a suggestion...
I would recommend putting VLC Media Player.  It was recommended as the best DVD player by Linux Format in the April 2006 issue.  You can get it from the repositories.

---

### Post by blackjack6.21.91 on 2006-07-06
Thank you.. vlc and mplayer are totally awesome.  Any reports on stability comparisons?  Should I use the VLC-firefox plugin or the mplayer one?

---

### Post by yosoyviejo on 2006-07-06
[QUOTE=blackjack6.21.91]When I try to launch totem-xine, it appears for just a bit and then disappears.[/QUOTE]

Have you tried [this](http://ubuntuforums.org/showthread.php?t=181948)?

---

### Post by blackjack6.21.91 on 2006-07-06
Resizing the logo worked.  Thank you.  But, just for the record, VLC rocks!

---

### Post by yosoyviejo on 2006-07-07
> **blackjack6.21.91 said:**
> Resizing the logo worked.  Thank you.  But, just for the record, VLC rocks!

You're welcome.

---

### Post by makoto149 on 2006-07-08
I got the exact same error and VLC didn't help. VLC would play the audio but not the video.  Xine player did the trick.

Blackjack, is the "you" in your quote intentional?  You might mean "your"??

---

### Post by blackjack6.21.91 on 2006-07-08
As long as you have a working video player!
> Blackjack, is the "you" in your quote intentional? You might mean "your"??
I'm afraid I don't know what you mean

Peace,
blackjack

---

