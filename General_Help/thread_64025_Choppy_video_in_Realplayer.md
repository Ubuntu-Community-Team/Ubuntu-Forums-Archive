---
title: "Choppy video in Realplayer"
date: 2005-09-09
forum: General Help
---

### Post by cbudden on 2005-09-09
Hello.  If i play a stream in realplayer, the video is very choppy, pausing every three ish seconds.  If i play it in xine, the video is stable.  How can i get this fixed in Real?

---

### Post by skoal on 2005-09-09
Hmm.  I would imagine since it occurs at routine intervals (every 3 seconds), that it has something to do with buffering midstream.  I have RealPlayer v10.0.2.608 from their website, and not the .deb (if there is one).

Can you provide a link to one website you're having these problems with?

Under Tools > Preferences > Playback, try changing "Buffer partial clip" to something _more_ than what it presently is.  Or, just don't use buffering at all ("Buffer Entire clip") and see if those pauses continue.  Of course, that would mean it will download the entire stream first.  That will at least help eliminate that possibility...

\\//_

---

### Post by cbudden on 2005-09-09
They are streams from bbc.co.uk news.  I am using 10.0.5.756.  The problem occurs with just the video, not the audio.  I tried turning on buffer entire clip but it has not made a difference.

---

### Post by skoal on 2005-09-09
I just tried playing those vids on BBC and the audio and video stream pretty smoothly for me @34kbps.

Just a quick question.  After you installed Realplayer as sudo (root), did you go through the setup process for a normal user?  If so, you should have a ~/.realplayerrc file.

Also, did you make a symbolic link in /usr/bin to the realplayer script (where you installed it).  If not, you need to since it sets some ENV variables.  For example,

```
skoal@morpheus://~ $ ls -l /usr/bin/realplay 
lrwxrwxrwx  1 root root 24 2005-09-05 22:59 /usr/bin/realplay -> /opt/RealPlayer/realplay
```

If not, make that link thusly: sudo ln -s /path/to/realplayer/install/realplay /usr/bin/realplay

note: don't symlink the "realplay.bin" file, just "realplay"...

\\//_

---

### Post by skoal on 2005-09-09
cbudden, by the way...

There are a few other things you can try (in this order):

1. Disable using the XV extension: Tools > Preferences > Hardware > remove X from "Use XV video".

2. Make sure you have the proper "Bandwidth" settings: Tools > Preferences > Connection.  You can try lower settings (or higher).

3. I ran across one thread which said by installing the "alsa-oss" compatibility libs, the video smoothed out.  Instead of "realplay", they used "aoss realplay".  To make that work smoothly, I suppose you could change the following (as root):

Toward the bottom of the '/path/to/realplayer/installation/realplay' script, make the following changes in an editor as root:

ORIGINAL:
# execute binary (and pass args), optionally running via catchsegv
REALPLAYBIN=$HELIX_LIBS/realplay.bin

NEW:
# execute binary (and pass args), optionally running via catchsegv
REALPLAYBIN="aoss $HELIX_LIBS/realplay.bin"

4. Install a lower revision of Realplayer (like the version I'm using).  I haven't run across any problems so far from various realplayer streams.

5. Check video driver config.  Update to newer version (if possible)...

\\//_

---

### Post by cbudden on 2005-09-09
[QUOTE=skoal]cbudden, by the way...

There are a few other things you can try (in this order):

1. Disable using the XV extension: Tools > Preferences > Hardware > remove X from "Use XV video".

2. Make sure you have the proper "Bandwidth" settings: Tools > Preferences > Connection.  You can try lower settings (or higher).

3. I ran across one thread which said by installing the "alsa-oss" compatibility libs, the video smoothed out.  Instead of "realplay", they used "aoss realplay".  To make that work smoothly, I suppose you could change the following (as root):

Toward the bottom of the '/path/to/realplayer/installation/realplay' script, make the following changes in an editor as root:

ORIGINAL:
# execute binary (and pass args), optionally running via catchsegv
REALPLAYBIN=$HELIX_LIBS/realplay.bin

NEW:
# execute binary (and pass args), optionally running via catchsegv
REALPLAYBIN="aoss $HELIX_LIBS/realplay.bin"

4. Install a lower revision of Realplayer (like the version I'm using).  I haven't run across any problems so far from various realplayer streams.

5. Check video driver config.  Update to newer version (if possible)...

\\//_[/QUOTE]
 Before i go through your suggestions i downloaded the thing i wanted to watch (click online) on windows then watched it back on Ubuntu, and the problem was still there, with the video being stored locally.

---

### Post by skoal on 2005-09-09
If it played fine in Windows, at least you can rule out any hardware related problems - slow proc, video card, et cetera.  Of course, that doesn't rule out any driver differences between the two.  

I guess you can rule out option 2 then if you played the stream locally.  Hopefully, 1 or 3 will fix it for you.

\\//_

---

### Post by cbudden on 2005-09-09
aoss realplay works great.  Will your file editing you suggested make the firefox plugin work aswell?

---

### Post by cbudden on 2005-09-09
Brilliant.  Thank you very much for you help skoal!  All nice and smooth now! Thanks again.

---

### Post by skoal on 2005-09-09
Sure thing, brother.  I guess the audio out of sync (or something else using the dsp device) was messing with your video stream.  I dunno.  Embedded streaming is all voodoo to me.  Glad you got it working...

\\//_

---

### Post by cbudden on 2005-09-10
:)

---

### Post by hiruzzolo on 2005-10-17
hi!I have the same problem in breezy,but your solution that worked for you didn't worked for me, I couldn't not open realplayer anymore.. How can I solve this? Tnx!

---

