---
title: "Setting Shoutcast Source from Line-In"
date: 2005-06-30
forum: General Help
---

### Post by njean on 2005-06-30
Hey all

First of all, sorry if I posted in the wrong area.

I'm trying to setup a shoutcast streaming source+server on the same (k)ubuntu Hoary machine, so I downloaded the server and source applications from shoutcast.com

I start the server and it's all ok, waiting for sources.

Then, when I try to edit th source config:

```

# this is a sample playlist file.
#
# the playlist contains one line per song file you wish to stream.  the paths
# should be absolute.
#
# if shuffle is off, the songs will play in order.
#
# the playlist is read once at startup, and cached to memory.  you may update
# the playlist in a running process by sending a kill -USR1.  The next track
# to play after the one currently playing will be from the new playlist.
#
# on linux, you may specify a playlist item of DSP:/dev/soundcard, where soundcard
# is the name of your audio device.  It's usually /dev/audio.  doing so will allow
# you to broadcast from a line input feed instead of mp3s on disk.
#
# the playlist ignores the first valid line.  Don't ask why.  
# Your playlist must have at least 2 entries.  if you only want to stream one file
# over and over again, then list it twice, including DSP sources.
#
# the following 2 lines are sample playlist lines.  you should replace them with
# actual mp3 files, being sure to adhere to all the content guidelines set forth in
# the .conf file!
/dev/dsp
/dev/dsp
```

I don't know what to put at the end of file in order to make him listen for the LINE-IN!

with dev/dsp on the server console I see that the stream goes removed because of no source...

help please !  :roll:

---

### Post by njean on 2005-06-30
up! help please!

---

### Post by keithacole on 2005-07-31
im trying to do the same exact thing... hit me on gaim...

how far have u gotten... i cant even record my sessons yet

---

