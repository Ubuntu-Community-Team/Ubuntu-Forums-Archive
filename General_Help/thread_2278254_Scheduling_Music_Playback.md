---
title: "Scheduling Music Playback"
date: 2015-05-15
forum: General Help
---

### Post by Kadaver on 2015-05-15
Hi,

Here is my scenario:

I need to be able to schedule the playing of a playlist of music at a certain time and then stop the music playing at another time. The music should repeat through the playlist if the time is longer than the selected playlist, it should also shuffle the music playback.

Now I had managed to do this on windows by using iTunes, and some .vbs files, but I'm needing to do this on Ubuntu if possible.

Any ideas would be most welcome, or to point me in the correct direction.

Thanks
W

---

### Post by TheFu on 2015-05-15
There may be a GUI way to do it, I just don't know that side of Linux. Hopefully someone else will respond. Maybe clementine can do this or amarok? I dunno. Sorry.

Anything is possible. Just write a little script ... That will depend on your ability and willingness.  Break down the problem into steps, write a tiny script to handle each part of that, then group all the steps into 1 script - bam - you are a poweruser and have exactly what you need.  

A few ideas:
* find a music player that works from the shell. It is much easier to automate things that way - maybe 1000x easier. I've seen client/server music server/player architectures for just this sort of need. xmms2?
* find a music player that supports playlists ... m3u is an easy platlist format to create in a script. Perhaps mplayer, if xmms2 doesn't do it.
* create a tiny script to get the list of all audio files you want into a playlist - perhaps something like "find /path/to/audio -type f -iname \*mp3 " - very easy.
* If you know how long the music in the playlist runs, you can randomize the playlist on that period - every 3 days, every day, every 12 hours ... using cron.
* Starting a program can happen with at, cron, or some alarm tool.  Audio is generally not allowed if the userid is not logged into the console. You can override that.  cron will be the hardest, since it really meant for use by media applications.
* To stop playback as a specific time, use **cron** or **at** or another alarm tool to kill the process playing the audio - this implies that you saved that PID for later use by the **kill** command.

So, with all that written I can say that I've done most of these things, just not all together.  Podcast to playback daily as my pre-wake-up music.  Every day the process randomizes a huge playlist.m3u file from a music collection, tho I only actually listen to it about 1 day a week.  Killing a task is pretty easy, much easier if you know the PID, which is returned in an environment variable when a process is started.  There are hundreds of examples for how to do this in /etc/init.d/* and store the value into a file.

---

### Post by tgalati4 on 2015-05-15
I wrote a series of scripts for GNAS, which stands for GNAS is Not a Announcement System for a county fairground.  I used the *at* command, which can be tricky--you need to *echo* the commands.  I will have to search for those scripts since the server is in storage until September.

Perhaps lay out the pseudo code or list the visual basic files and we can fill in the pieces that are missing.

---

### Post by QDR06VV9 on 2015-05-15
Audacious through the Alarm settings I think will do that what you need if I'am understanding.
You can also create a playlist in those same settings see the attached pic.
Kind Regards

---

### Post by Kadaver on 2015-05-15
Hi,

Awesome help guys, I'm not that great with the scripts but I'm always willing to learn something new in Ubuntu. I have something to work with now and a direction.

Will give them all go this afternoon to see which would work the best for me. I'll upload the vbs files a little later as I'm not near the computer with the files on right now.

Again, thanks a load guys.
W

---

### Post by TheFu on 2015-05-16
> **runrickus said:**
> Audacious through the Alarm settings I think will do that what you need if I'am understanding.
You can also create a playlist in those same settings see the attached pic.
Kind Regards

That's brilliant. I've used audacious before.
[http://ubuntuforums.org/showthread.php?t=903962](http://ubuntuforums.org/showthread.php?t=903962)
Tried it out. Audacious died, but kept playing. Had to **kill -9** it. Normal kill didn't do anything.

---

### Post by QDR06VV9 on 2015-05-16
> **TheFu said:**
> That's brilliant. I've used audacious before.
[http://ubuntuforums.org/showthread.php?t=903962](http://ubuntuforums.org/showthread.php?t=903962)
Tried it out. Audacious died, but kept playing. Had to **kill -9** it. Normal kill didn't do anything.
Thank You Sir!
I saw where you use lubutnu I have not tried that desktop for quite some time now!
But there is this PPA: [https://launchpad.net/~nilarimogard/+archive/ubuntu/webupd8](https://launchpad.net/~nilarimogard/+archive/ubuntu/webupd8) ,that adds more stable addons and such for audacious.
If you are inclined:D
Kind Regards

---

### Post by lusiyen on 2015-05-16
Perhaps lay out the pseudo code or list the visual basic files and we can fill in the pieces that are missing > **tgalati4 said:**
> I wrote a series of scripts for GNAS, which stands for GNAS is Not a Announcement System for a county fairground[.]("http://www.yeniulke.net/teknoloji/tubidy-m3-indir-tubidy-muzik-indir-bedava-mp3-mp4-indir-h2328.html")  I used the *at* command, which can be tricky--you need to *echo* the commands.  I will have to search for those scripts since the server is in storage until September[.]("http://www.yeniulke.net/teknoloji/tubidy-m3-indir-tubidy-muzik-indir-bedava-mp3-mp4-indir-h2328.html")

Perhaps lay out the pseudo code or list the visual basic files and we can fill in the pieces that are missing.

---

### Post by Kadaver on 2015-05-16
The solution was actually so simple, I'm going to go with audacious. It's working perfectly for what I need to do here.

It has the option to repeat and shuffle for all songs in the playing playlist, I can set it to start with the Alarm plugin, which also has a fade out after a period of time. This is really going to make so much easier. 

Now off to purchase some Gigabyte Brix for the project.

---

### Post by tgalati4 on 2015-05-17
If you don't need a full PC at the playback location, I have had good experience with these devices for playback.  [http://www.barix.com/products/exstreamer-family/](http://www.barix.com/products/exstreamer-family/)

You only need one Linux server that can support several remote playback devices.  Each device supports webpage control as well as using CURL to send control commands through scripts.  It makes for a simple/cheap network audio playback system.  The sound is not time-aligned, but if the endpoints are far from each other, that is not a problem.

---

### Post by Kadaver on 2015-05-17
That's not to bad actually, my scenario is that of having to play music in several building foyers. They based all over the city, they have internet connection for remote access at each location and audio equipment is already installed.

This one seems to be pretty close to something I will look into. [http://www.barix.com/products/exstreamer-family/barix/Product/show/exstreamer-storeplay/]("http://www.barix.com/products/exstreamer-family/barix/Product/show/exstreamer-storeplay/")

---

