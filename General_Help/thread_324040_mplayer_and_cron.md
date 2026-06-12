---
title: "mplayer and cron"
date: 2006-12-23
forum: General Help
---

### Post by evaristegalois on 2006-12-23
I run Ubuntu 6.06 with linux kernel 2.6.15-27-386 on an IBM Thinkpad laptop.

Here is my question: I want to schedule recordings of internet audio streams (public radio) and automatically convert them to mp3 files for my ipod. I use mplayer to dump the audio stream into a ram file. Then I use mplayer again to convert the ram file to a wav file. Then lame to convert the wav file to a mp3 file.

All of this works without a hitch except the step from ram to wav. The odd thing is that this can easily be done on the command line:

/usr/bin/mplayer -vo null -vc dummy -af resample=44100 -ao pcm:file=/directory/test.wav /directory/test.ram

Yet when I put this line verbatim into my crontab file:

52 0 23 12 * /usr/bin/mplayer -vo null -vc dummy -af resample=44100 -ao pcm:file=/directory/test.wav /directory/test.ram

The result is a wav file which is interrupted after ten seconds. You always hear the first ten seconds, no matter how long the original file is, and then nothing.

What could it possibly be about this command running in cron that doesn't make it work, as opposed to running it on the command line?

Your help is appreciated!

---

### Post by taurus on 2006-12-23
Why don't you create a file called recording.sh and add that line to it!!!

```

#!/bin/bash
/usr/bin/mplayer -vo null -vc dummy -af resample=44100 -ao pcm:file=/directory/test.wav /directory/test.ram

```
Then, change the permission so it is an executable.

```
chmod 755 recording.sh
```
Now, all you need is to add recording.sh to your /etc/crontab...

---

### Post by evaristegalois on 2006-12-23
good thought. I already thought of that, though. No matter how you tweak it: when crontab executes the command, even through a shell script, the ram > wav conversion does not work, even though directly off the command line it does. I know that cron jobs run from a different kind of shell than command line commands. For example, I need to use /usr/bin/mplayer as my command in cron while on the command line just mplayer is enough. What are the essential differences between a command line running a command and cron doing it? What diagnostic methods are there to get to the bottom of this?

--evaristegalois

---

