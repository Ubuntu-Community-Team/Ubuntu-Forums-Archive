---
title: "Project for Recording Radio Streams :) Help with crontab..."
date: 2008-02-19
forum: General Help
---

### Post by lambono on 2008-02-19
Hi,
I am currently working on a project That will allow a user to 
1.Log into a website (Ubuntu LAMP)
2.Schedule a Radio Stream to be recorded (From a list of stream addresses)
3.These streams will be automatically recorded and saved as an MP3 file for the user to retrieve. 

I have written a small shell script that will dump the stream data using mplayer
and convert this to WAV and then MP3 using LAME and mplayer...

#!/bin/bash

SHOWNAME=$1
STREAMADDRESS=$2
USERNAME=$3
DURATION=$4
STATIONNAME=$5

DUMPLOCATION='/var/www/dumps/'
USERDIR=$DUMPLOCATION$USERNAME/

# Check the User directory exists
if [ -d $USERDIR  ]; then
   echo User Directory Exists
else
   mkdir $USERDIR
fi

if [ -d $USERDIR  ]; then
   # Dump the stream using MPlayer
   mplayer -dumpstream -playlist $STREAMADDRESS -dumpfile "$USERDIR$SHOWNAME".dump -vc dummy -vo null &

# -vc dummy and -vo null switches tells MPlayer to disregard any video content. This helps increase performance

# Store the mplayer processID
MPLAYPROCESS=$!

# Sleep for the length of the show
sleep $DURATION

# Kill mplayer when show is finished 
echo Killing process $MPLAYPROCESS
kill $MPLAYPROCESS

fi


# If the .dump file is created... 

if [ -f $USERDIR$SHOWNAME.dump ]; then
   echo dump exists

# Create the .mp3 file using LAME and MPlayer 
mkfifo $USERDIR$SHOWNAME.pipe

lame -h -v -b 64 --silent --tt $SHOWNAME --ta "SaveTheRadio.net" --tl "${STATIONNAME}" --ty "2008" --tc "This podcast was recorded for the personal use of "$USERNAME" by SaveTheRadio.net" "$USERDIR$SHOWNAME.pipe" "$USERDIR$SHOWNAME".mp3 & mplayer -vc dummy -vo null -ao pcm:file="$USERDIR$SHOWNAME.pipe" "$USERDIR$SHOWNAME".dump

fi

# If .mp3 file is created remove the temp .pipe and .dump files
if [ -f $USERDIR$SHOWNAME.mp3 ]; then
   echo MP3 exists
   rm $USERDIR$SHOWNAME.pipe
   rm $USERDIR$SHOWNAME.dump
fi


When the user schedules a show through the website it is added in the crontab
eg

35 18 * * * /home/scripts/recordJob.sh The_Show_Name [http://www.bbc.co.uk/northernireland/realmedia/ru-live.ram](http://www.bbc.co.uk/northernireland/realmedia/ru-live.ram) ben 300 BBC_ULSTER > /tmp/phpCronLog.log 

This then calls the script when required and the mp3 is placed in the users directory. 

I have tested this with a few different streams and it works. 

However I am having a strange problem with the stream [http://www.bbc.co.uk/radio2/wm_asx/aod/radio2.asx](http://www.bbc.co.uk/radio2/wm_asx/aod/radio2.asx) for BBC radio 2.
For some reason if I invoke the script directly from the command line it works... but using the cron job it will create the dump file but not the MP3. Any idea why this would happen!??? What is the difference in using cron 
Invoking the script from the crontab works fine of other streams like  [http://www.bbc.co.uk/northernireland/realmedia/ru-live.ram](http://www.bbc.co.uk/northernireland/realmedia/ru-live.ram)

If you could provide any help with this it would be great! 

Also, If you are interested in this project, or know of any good links that may be useful to me please let me know! 

Thanks,
Lambono

---

### Post by lambono on 2008-02-19
Ok, it works sometimes...
What would be the best way to handle errors etc so that I get a better success rate.

Thanks for the help :)

---

### Post by sethjvm on 2008-02-20
This page may be of help to you.

[http://grimthing.com/archives/2004/05/20/recording-streaming-audio-with-mplayer/](http://grimthing.com/archives/2004/05/20/recording-streaming-audio-with-mplayer/)

---

### Post by lambono on 2008-02-25
Hi sethjvm,
Thats a usefull link.
Thanks!

---

### Post by lambono on 2008-02-29
Are any other people intesested in this type of project?

---

### Post by BertP on 2008-03-07
I am a Linux/Ubuntu noob,  so I don't know how I could be of help but I am  interested in gaining the ability to record audio streams

If your interested in talk radio streams, check out this website::
[http://streamingradioguide.com/streaming-radio.php?format=1&radio-format=News/Talk](http://streamingradioguide.com/streaming-radio.php?format=1&radio-format=News/Talk)

---

