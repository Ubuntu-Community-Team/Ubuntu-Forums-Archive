---
title: "Can't play full DVD movies, just parts at a time"
date: 2006-08-08
forum: General Help
---

### Post by JimS on 2006-08-08
...
Just installed Dapper on my Toshiba notebook pc
and am trying to play commercial DVD movies.
I get the icon when the DVD is loaded.
I can play a single vob-files.
But I can't get the movie to play beginning to end
w/o starting each vob.
I get same results using both VLC and Mplayer.

I would like to be able to play DVD movies,
simply by clicking once or twice to get them started.
Then they play all the way to the end, not stopping
at the end of each vob.  That is what I want.

Any help will be much appreciated.
Thanks in advance.
...

---

### Post by timetunnel on 2006-08-08
Can you be more specific about *how* and *why* you played vob files? Usually DVD playback doesn't involve starting the vob files from the disc by yourself. You have to tell the player to play the *DVD* instead of a *file*. In xine-ui, for example, you press key "G" to show the control panel, then press "DVD" there and it should start. In VLC player, you do "File->Open media", go to tab "Volume", enter "/dev/dvd" in the field for "Devicename", and "OK" should do the job.

---

### Post by JimS on 2006-08-08
...
I played individual vob files because I could
not get any program to play the entire DVD
movie, much less do it automatically.

I just put a DVD in my pc and Totem putted up.
Error msg: Totem could not play dvd:///media/cdrom0',
No URI handler implemented for "dvd".

Thanks to your directions I was able to get VLC
to play the complete DVD.  I went to File >
Open Disc > Disc Tab > and typed /dev/dev at
Open at top.
Trouble is I need to go thru this whole long
procedure everytime I want to play a DVD.
No thank you.

Wow!!  Just installed Totem-xine and now Totem
loads up and runs the movie DVD I just put in
my pc.  It will also changes chapters and show subtitles.
Now that is what I wanted.

Thanks for the hint about xine.

---

### Post by timetunnel on 2006-08-08
> Trouble is I need to go thru this whole long
procedure everytime I want to play a DVD.

Me too. And Totem never did it for me, because I had lots of problems with it. xine-ui (not the Totem plugin, but a seperate Xine player) always worked best for me. Compared to Totem and VLC, it just works - at least for me.

Enjoy your DVDs :-)

---

