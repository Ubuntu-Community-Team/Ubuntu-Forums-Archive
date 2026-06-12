---
title: "crontab doesn't work with gorecord"
date: 2008-06-28
forum: General Help
---

### Post by Verlager on 2008-06-28
I have a Plextor ConvertX px-TV402U usb video capture device which has a utility driver, gorecord.

gorecord works fine from the command line:
```

rmack@tojo:~$ gorecord -input 2 -duration 3120 -tvchan ntsc-cable:43 -bitrate 1750 test-1.avi
/dev/video0 is a GO7007 device at USB address 4-1:1.0
Attempting to determine audio device...using audio device /dev/dsp1
Using input port Tuner
Warning: no video standard specified; using NTSC
Capturing video at 640x480, 29.97 FPS
 00:06:53.84  Frames: 12403  AVI size: 162MB  A-V:  -45.91ms  Video:  1610kbps

    Video data written to file: 90450313 bytes of MPEG4
    Audio data written to file: 79462656 bytes of uncompressed PCM
    AVI file format overhead  : 602639 bytes
    Total file size           : 170515608 bytes
    Total A/V correction      : -16128 bytes

```

**But when I add it to a cron job, it bombs after writing 142206 bytes:**

rmack@tojo:~$ cat cron_tab 
22 3 28 6 6 gorecord -input 2 -duration 3120 -tvchan ntsc-cable:43 -bitrate 1750 test.avi

rmack@tojo:~$ crontab cron_tab

rmack@tojo:~$ ls -l *.avi
-rw-r--r-- 1 rmack rmack 170515608 2008-06-28 03:39 test-1.avi
**-rw-r--r-- 1 rmack rmack    142206 2008-06-28 03:22 test.avi**

---

### Post by Gunman1982 on 2008-06-28
MAybe you should log the output from your gorecord by adding the string ```
 >> $HOME/crontab.log 2>&1
``` behind ```
22 3 28 6 6 gorecord -input 2 -duration 3120 -tvchan ntsc-cable:43 -bitrate 1750 test.avi >> $HOME/crontab.log 2>&1
``` after that just execute 'touch $HOME/crontab.log' so that the file is created and wait until cron executes your gorecord.

Explanation:
'>>' <- appends the standardoutput of a program to an existing file
'>' <- does the same but creates a new file (eventually overwrites a file if it already exists)
'2>&1' <- not only take the standard output but the error output too

---

### Post by Verlager on 2008-06-28
Thank you! Your suggestion allowed me to successfully debug the gorecord output. Turns out I am not pathed to my home dir. This sample line from **crontab -l** shows the correct syntax:

_11 15 28 6 6 ~/record_coax.sh cSpan 44 1 >> $HOME/crontab.log 2>&1_

I have two gorecord shell scripts, one each for the coax and composite connections.

rmack@tojo:~$ **cat record_coax.sh **
#!/bin/bash
if [[ $# -lt 2 ]]; then
        echo "Usage: $0 {filename (no suffix)} {channel} {record time in minutes}"
    exit 1
fi

bitrate=1750
mode=ntsc
#format=mpeg2-dvd
format=mpeg2
duration=`expr $3 \* 60`
input=2
channel=$2

gorecord -input $input -duration $duration -tvchan ntsc-cable:$channel -bitrate $bitrate -format $format $1.avi

#copy recently created clip to basement server
cp $1.avi /media/500GB-1/video/

---

