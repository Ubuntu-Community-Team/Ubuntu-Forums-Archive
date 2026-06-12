---
title: "Cron Job to convert to MP3"
date: 2008-04-04
forum: General Help
---

### Post by GiorgosR on 2008-04-04
Hi guys,

I just set up my ubuntu server and I am struggling with a cron job. To start from the beggining, I want to record a stream of audio, convert it to mp3 and put it on my webserver so I can download it from anywhere.

I am using this scripts (that I modified from little gems I found on the internet):
**The Scripts**

# ==> Script 1 (recordRadio.sh) <==
#!/bin/sh

# Get recording time from command line
if test -z "$1"
then
# No command line argument for time, use default time
recording_time=1500
else
# Use recording time that was passed in
recording_time=$1
fi

# Create directory for stream if it doesn't exists
# test -d /opt/streams/`date +%Y%m%d` || mkdir /opt/streams/`date +%Y%m%d`

# Schedule mplayer to rip stream to file
nohup mplayer [http://sportfm.live24.gr/sportfm7712](http://sportfm.live24.gr/sportfm7712) -cache 4096 -cache-min 10 -dumpstream -dumpfile /var/www/recordings/PanKarp.asf -vc dummy -vo null &

# Get PID of this mplayer process
mplayer_pid=$!

# Schedule process to kill mplayer after designated time
nohup /home/george/end_mplayer.sh $mplayer_pid $recording_time &
# ==> END OF SCRIPT <==

This script works well and I end up with a nice ASF file in my directory. As you can see, it then calls a second script

==> Script2 (end_mplayer.sh) <==
#!/bin/bash
NOW=$(date +"%j-%a%d%b")
mplayer_pid=$1
sleep_time=1

MP3FILE=/var/www/recordings/PanKarp$NOW.mp3
sleep $sleep_time
kill $mplayer_pid
mplayer -ao pcm:file=/var/www/recordings/PanKarp.wav /var/www/recordings/PanKarp.asf
/usr/bin/lame -m s /var/www/recordings/PanKarp.wav $MP3FILE > /var/www/recordings/error.log
# ==> END OF SCRIPT <==

**The Problem**
The above will convert the ASF to WAV (which it does nicely), but when it gets to lame converting the WAV, it only does about 2-3 seconds and then ... kaput!

If I run the scripts from shell (i.e. sh /home/george/end_mplayer.sh), then everything goes fine. I am struggling to see what the problem is and I have no more grey matter left.

I'd really aprpeciate any pointers to a solution.

Cheers,

Giorgos

---

### Post by monraaf on 2008-04-04
> **GiorgosR said:**
> 
sleep_time=1
sleep $sleep_time


Maybe your script should sleep a little longer?

---

### Post by GiorgosR on 2008-04-04
Thanks for the quick reply monraaf.

I am executing it in the background on purpose. The 2nd script will wait for a set period of time and then kill the mplayer instance. This is because I want only xxx seconds to be recorded.

On the 2nd script, the conversion to WAV works fine, it is the conversion to MP3 that goes belly up.

---

### Post by monraaf on 2008-04-04
Yes, that came to my mind after I replied. See my edited reply.

---

### Post by GiorgosR on 2008-04-04
> **monraaf said:**
> Yes, that came to my mind after I replied. See my edited reply.

Hmm, yes, it should. This is just left-over from me debugging the thing, as I do not need to to wait at all at the moment. I have an WAV file ready, so I do not need to wait for the WAV conversion (or the ASF capture).

But thanks for your help.

---

