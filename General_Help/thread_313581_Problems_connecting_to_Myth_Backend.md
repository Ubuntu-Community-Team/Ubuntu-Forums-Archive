---
title: "Problems connecting to Myth Backend"
date: 2006-12-06
forum: General Help
---

### Post by BIGtrouble77 on 2006-12-06
Whenever I go into mythftont end it says that it cannot connect to the backend server, but the backend server is running on that same machine.  I tried changing the IP address to 127.0.0.1, localhost, and the machine's IP.  Nothing works.  Myslq connection appears to be working fine, capture card is working and the channels are all updated.

I just need some suggestions for things to try.  I'm out of ideas.

---

### Post by superm1 on 2006-12-06
Hi,

Have you taken a look at the troubleshooting section in the wiki, particularly to check if the backend is running?

[https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend_Desktop#head-2ca13596b08d7736a909ba52b4bffd2b547fb4f4](https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend_Desktop#head-2ca13596b08d7736a909ba52b4bffd2b547fb4f4)

---

### Post by BIGtrouble77 on 2006-12-06
Thanks for the link, I'll try some of the suggestions tonight.

---

### Post by BIGtrouble77 on 2006-12-06
I'm still having trouble.  My capture card is detected by the software so i'm puzzled why it's not working here.  Here's my error log:
```
2006-12-06 14:39:48.980 New DB connection, total: 1
2006-12-06 14:39:49.005 Connected to database 'mythconverg' at host: 192.168.0.4
2006-12-06 14:39:49.010 Current Schema Version: 1160
Starting up as the master server.
2006-12-06 14:39:49.018 New DB connection, total: 2
2006-12-06 14:39:49.038 Connected to database 'mythconverg' at host: 192.168.0.4
2006-12-06 14:39:49.042 EITHelper: localtime offset -5:00:00 
2006-12-06 14:39:49.046 TVRec(1) Error: Problem finding starting channel, settin
g to default of '3'.
2006-12-06 14:39:49.047 ChannelBase(1) Error: InitializeInputs(): 
                        Could not get inputs for the capturecard.
                        Perhaps you have forgotten to bind video
                        sources to your card's inputs?
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
2006-12-06 14:39:49.050 Main::Starting HttpServer
2006-12-06 14:39:49.052 New DB connection, total: 3
2006-12-06 14:39:49.072 Connected to database 'mythconverg' at host: 192.168.0.4
2006-12-06 14:39:49.075 Main::Registering HttpStatus Extension
2006-12-06 14:39:49.082 mythbackend version: 0.20.20060828-3 www.mythtv.org
2006-12-06 14:39:49.083 Enabled verbose msgs:  important general
2006-12-06 14:39:49.084 AutoExpire: Found 0 recorders w/max rate of 0 MiB/min
2006-12-06 14:39:49.085 AutoExpire: Required Free Space: 1.0 GB w/freq: 10 min
2006-12-06 14:40:04.076 MainServer::HandleAnnounce Monitor
2006-12-06 14:40:04.081 adding: DVR as a client (events: 0)
2006-12-06 14:40:04.082 MainServer::HandleAnnounce Monitor
2006-12-06 14:40:04.083 adding: DVR as a client (events: 1)
2006-12-06 14:40:05.796 MainServer: HandleRemoteEncoder(cmd GET_STATE) Unknown e
ncoder: 1, exiting

```

---

### Post by superm1 on 2006-12-07
Well what card do you have?  Are you sure the card is functioning?  Also, did you remember to bing the cards input to a video source like it is indicating?

---

### Post by fatalfurry on 2006-12-07
Are you running the backend and frontend at the same time? They both need to be running.

---

### Post by BIGtrouble77 on 2006-12-07
First off, yes, the backend and front end are running.  I'm using a PVR-250 card.  I configured it with ITV I believe.  The myth setup detects the card at video0.  I created a profile called pvr250 in myth.  

So I'm very confused why it's saying that it can't find the card.  I read some other threads that say you need to upgrade the video card drivers, which I did.  I also reran the command to populate the database with channel info.  Still won't connect.

---

### Post by superm1 on 2006-12-07
First: Verify that your pvr series card is functioning.
```
cat /dev/video0 > ~/test.mpg
```
press <ctrl>+c after about 5 seconds. 
Attempt to play this in a media player: mplayer, xine, vlc, totem  -whatever your favorite is.  If there is video playback, the card driver is working (at least for the most part).

Second:
type 
```
dmesg
```
Look inbetween the blocks START_IVTV and END_IVTV.  If there are any firmware loading issues, tuner setting issues, driver loading issues - anything.  If your not sure, post between those two blocks here.

Third:
A very common error with the PVR-series cards is to choose the wrong type of card in mythtv-setup.  You need to choose the PVR-XXX  series card option under the capture cards page.  The common error is to choose standard v4l device.  Here is a screenshot of the option you should be choosing: [https://help.ubuntu.com/community/MythTV_mythtvsetup?action=AttachFile&do=get&target=screenshot12.png](https://help.ubuntu.com/community/MythTV_mythtvsetup?action=AttachFile&do=get&target=screenshot12.png)

Also, once you bind it correctly to an output, you should have the output connections page indicating this:
[https://help.ubuntu.com/community/MythTV_mythtvsetup?action=AttachFile&do=get&target=screenshot14.png](https://help.ubuntu.com/community/MythTV_mythtvsetup?action=AttachFile&do=get&target=screenshot14.png)


Here is the walkthrough of mythtv-setup from the mythtv wiki pages on help.ubuntu.com if you have anything else you were confused about:
[https://help.ubuntu.com/community/MythTV_mythtvsetup](https://help.ubuntu.com/community/MythTV_mythtvsetup)

---

### Post by BIGtrouble77 on 2006-12-07
superm1,
you kick ***.  I did not have the video binded correctly so your suggestion and screenshot helped.  I finally have video in myth.  

Now I just have to figure out why sound doesn't work, how to add deinterlacing and why my channels arenting matching the correct profile I downloaded.  Sound, btw, does work when I cat video0.

Anyway, thanks so much.  The problems I needed resolved in this thread are fixed!

-BT

---

### Post by superm1 on 2006-12-07
For sound, try going into mythtv frontend settings.  Choose the general settings, and you will come to a page that lists audio device.
change /dev/dsp to ALSA:default
and /dev/mixer to ALSA:default

Retry after that.

---

### Post by BIGtrouble77 on 2006-12-07
that worked too, thanks a lot!

---

