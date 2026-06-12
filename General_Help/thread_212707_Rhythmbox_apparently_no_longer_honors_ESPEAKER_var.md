---
title: "Rhythmbox apparently no longer honors ESPEAKER variable"
date: 2006-07-10
forum: General Help
---

### Post by haynold on 2006-07-10
Hello:

I had an issue in Breezy with Rhythmbox not honoring the --espeaker option and worked around it by using the ESPEAKER environment variable. After upgrading to Dapper it seems that Rhythmbox doesn't honor this variable any more either. Does someone of you guys know what's going on and how to fix it?

Best,

        Oliver

---

### Post by carey on 2006-12-13
Yeah, I'm having problems with this also.

I can do this with mplayer:

export ESPEAKER=10.0.0.1:5001
mplayer music.ogg -ao esd

I have esd listening on that machine, and mplayer forwards that sound and it all works great! Thing is, I don't like mplayer.

But with rhythmbox:

rhythmbox --espeaker=10.0.0.1:5001

It just ignores that and plays that sound locally regardless! I tried the --enable-sound option too (to enable GNOME/esd sound or something) but it didn't make any difference either.

So how to play sound remotely with Rhythmbox, or other apps too? Maybe with Gstreamer? Hmm?

---

### Post by carey on 2006-12-13
Hey! I fixed it!

I just ran: gstreamer-properties

And selected "ESD" as the Audio Default Output Plugin.

Now the command: rhythmbox --espeaker=10.0.0.1:5001 works just fine.

Of course replace 10.0.0.1:5001 with the IP and port of the machine that is running your ESD server

To make ESD listen do (whatever port you want):

esd -public -tcp -port 5001

then connect to it as above and enjoy remote sound.

Hope that helps someone.

---

### Post by carey on 2006-12-13
Actually it was working because I had done

export ESPEAKER=10.0.0.1:5001

In a new shell without that exported, the --espeaker command doesn't seem to work for me. Probably doing something wrong there, oh well, at least I can get it working now.

---

