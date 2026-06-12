---
title: "Rhythmbox crash when play"
date: 2007-05-30
forum: General Help
---

### Post by Elvenfoot on 2007-05-30
Hi
I just installed the Feisty Fawn on the same partition as Vista, everything was going nice, as the ntfs-3g can read/write de vista sata partition normally.

But when i tryed to read a song from Vista partition on rhythmbox it just crash, i tryed wma and mp3 files and both of them crashes the rhythmbox when i press play. (or when i click on it twice).

I though it was a partition problem but the Totem Video Player plays the song normally. I also tryied the Exaile and the Listen Media Player and both of them had the same problems.

I also tryied remove and re-install the rhythmbox using apt-get, but that problem persisted.

Im using Ubuntu Feasty Fawn with all upgrades, the sound codecs was downloaded using the last automatix2 version (i downloaded it today).

Thanks for helping!

---

### Post by jamesjtucker on 2007-05-30
Automatix is sort of a bad word to some here on the forums, and be careful next time you run an upgrade... it broke my feisty install. Just an FYI on that. 

  Try running rhythmbox from the command line and seeing if it gives any useful errors when it crashes... this is typically the best way to see why the program has died. 
  Also, can you play mp3/wma/ogg/wav/etc files when they are on your ubuntu partion?

---

### Post by Elvenfoot on 2007-05-30
Hi, thanks for helping

First i tryied running a mp3 file from ubuntu partition, the same error happened.

Then i opened it on terminal, the error was this:

Falha de segmentação (core dumped)

My ubuntu is in Portuguese, the english error is Segmentation Fault.


And the upgrade i made it using the ubuntu upgrader, but rhytmbox was not working before the upgrade.

---

### Post by jamesjtucker on 2007-05-30
segfaults are typically VERY bad :) 
I know that this isnt a very great solution, but are you particularly tied to rhythmbox? When i was on gnome, i used to prefer listen: [http://www.listen-project.org/](http://www.listen-project.org/)
   Are there other problems with the system? Perhaps you had some issues with the upgrade or somthing? The rhythmbox developers may want to see the core file generated as well... perhaps a post in their forums might help?

---

### Post by flightmaker on 2007-06-05
I've got the same problem, running with KDE on Feisty. I've sent the messages from a shell to [email]rhythmbox-devel@gnome.org[/email]

I'm not a member there so it's awaiting the moderator.

---

### Post by flightmaker on 2007-06-06
Try disabling the plugins especially the visualisation and then

sudo apt-get install libgnomevfs2-extra

Mine is now working.

---

### Post by heatherkane on 2007-07-06
Hello. I seem to be having the same issue with rhythmbox, and it is happening in banshee as well. 

Here is the output from banshee when it crashes (rhythmbox's output is very similar - ie. sag. fault): 
```
** ERROR **: file mp3-c.c: line 518 (III_huffman_decode): assertion failed: (i <= SSLIMIT * SBLIMIT)
aborting...
Segmentation fault (core dumped)
``` 

 I've tried updating ibgnomevfs2-extra, but i already had the latest version. It always crashes at the same place in the same song, however, when I play it from the command line using 'mpg321' it works. 

I'm running Xubuntu 7.04, but my boyfriend who is running Ubuntu 7.04 seems to be having the exact same issue. 

Thoughts?

Thanks!! :KS

---

### Post by flightmaker on 2007-07-07
Have you tried disabling the plugins before attempting to play any music?

---

### Post by balleyne on 2007-07-11
I've had the exact same problem as heatherkane with banshee/rhythmbox crashing during the exact same part of the exact same song (amongst other songs, that's just the only one that I have pinpointed the "crash spot" for).

I've tried disabling all of the plugins in Banshee, and still I get

```
** ERROR **: file mp3-c.c: line 518 (III_huffman_decode): assertion failed: (i <= SSLIMIT * SBLIMIT)
aborting...
Segmentation fault (core dumped)
```

Any idea what this could be?

---

### Post by balleyne on 2007-07-11
Found something else - does **not** crash in XMMS.

What do rhythmbox and banshee have in common that xmms doesn't have? Gnome? Gstreamer? I'm not terribly familiar with this territory...

---

### Post by stephantom on 2007-07-24
This is a GStreamer related issue. It's already been fixed in SVN, so just wait for the next updates or build it yourself.
For reference: [https://core.fluendo.com/gstreamer/trac/ticket/18](https://core.fluendo.com/gstreamer/trac/ticket/18)

---

### Post by balleyne on 2007-07-24
Great! Glad it's been fixed, I can be patient. I was just wondering whether or not I'd have to file a bug report somewhere...

Thanks :)

---

### Post by Hilko on 2007-09-11
> **flightmaker said:**
> Have you tried disabling the plugins before attempting to play any music?

This worked for me, I just upgraded to feisty, then rhythmbox crashed whenever i pressed the 'play' button. Then I did: Menu -> edit -> plugins... I removed all checkmarks, now it works again. thanks!

---

### Post by balleyne on 2007-11-01
Bah, it appears that the updates didn't make it int Gutsy :(

---

### Post by balleyne on 2008-04-23
But it seems to be fixed in Hardy - hooray!

---

