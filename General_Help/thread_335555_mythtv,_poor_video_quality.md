---
title: "mythtv, poor video quality"
date: 2007-01-10
forum: General Help
---

### Post by Green_Star on 2007-01-10
Finally i configured mythtv on my EDGY, it is working fine, but video quality is really bad. If i take a sample video file (cat /dev/video0 > /tmp/test.mpg) and play that in mplayer it is really good quality, i can even watch live tv in vlc with very good quality. But only problem is with mythtv. it is giving really bad quality of video (more blue in the video), how can i fix this ? by installing any kind of codecs or something? please explain in detail (I am newbie to ubuntu linux)

attached screen shots for your reference.

In mythtv
[[IMG]http://img487.imageshack.us/img487/9482/inmythtvww4.th.png[/IMG]](http://img487.imageshack.us/my.php?image=inmythtvww4.png)


In VLC player
[[IMG]http://img487.imageshack.us/img487/3563/invlcch4.th.png[/IMG]](http://img487.imageshack.us/my.php?image=invlcch4.png)

---

### Post by reclusivemonkey on 2007-01-10
Erm not sure why you are getting this. I *think* mythtv uses mplayer to record/play tv so if its fine in mplayer, it should be fine in myth. Has mythtv tuned everything correctly? You've not changed any mythtv settings?

---

### Post by Green_Star on 2007-01-11
Thanks reclusivemonkey,

I did not changed any of settings. I guess mythtv tuned correctly. If you doubt please let me know where I need to check these settings. here is the log i got for mythfrontend, i bolded the error which i believe it belongs to video....

> :~$ mythfrontend
X Error: BadDevice, invalid or uninitialized input device 157
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 157
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
2007-01-11 05:47:16.792 Using runtime prefix = /usr
2007-01-11 05:47:16.806 Gnome-Screensaver support enabled
2007-01-11 05:47:16.807 DPMS is active.
2007-01-11 05:47:17.089 New DB connection, total: 1
2007-01-11 05:47:17.101 Connected to database 'mythconverg' at host: localhost
2007-01-11 05:47:17.105 Total desktop dim: 1280x1024, with 1 screen[s].
2007-01-11 05:47:17.111 Running in a window
2007-01-11 05:47:17.112 Using screen 0, 1280x1000 at 0,0
2007-01-11 05:47:17.155 Current Schema Version: 1160
2007-01-11 05:47:17.155 mythfrontend version: 0.20.20060828-3 [www.mythtv.org](www.mythtv.org)
2007-01-11 05:47:17.155 Enabled verbose msgs:  important general
2007-01-11 05:47:20.467 Total desktop dim: 1280x1024, with 1 screen[s].
2007-01-11 05:47:20.469 Running in a window
2007-01-11 05:47:20.469 Using screen 0, 1280x1000 at 0,0
2007-01-11 05:47:20.470 Switching to wide mode (Minimalist-wide)
2007-01-11 05:47:20.953 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
lirc_init failed for mythtv, see preceding messages
2007-01-11 05:47:22.285 Joystick disabled.
2007-01-11 05:47:22.640 Loading from: /usr/share/mythtv/themes/default/base.xml
2007-01-11 05:47:23.268 Registering Internal as a media playback plugin.
2007-01-11 05:47:55.241 New DB connection, total: 2
2007-01-11 05:47:55.241 Connected to database 'mythconverg' at host: localhost
2007-01-11 05:47:55.289 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2007-01-11 05:47:55.400 Using protocol version 31
2007-01-11 05:47:58.858 TV: Attempting to change from None to WatchingLiveTV
2007-01-11 05:47:58.859 Using protocol version 31
2007-01-11 05:48:01.418 DPMS Deactivated 
[B][COLOR="Navy"][mpeg @ 0xb73c4500]Parser not found for Codec Id: 94210 !
2007-01-11 05:48:01.748 AFD: Opened codec 0x8583250, id(MPEG2VIDEO) type(Video)[/COLOR][/B]
2007-01-11 05:48:01.786 AFD: Opened codec 0x855dc90, id(MP2) type(Audio)
2007-01-11 05:48:02.107 Opening OSS audio device '/dev/dsp'.
2007-01-11 05:48:02.323 VideoOutputXv: XvMCTex: Init failed
2007-01-11 05:48:02.324 VideoOutputXv: XVideo Adaptor Name: 'ATI Radeon AVIVO Video'
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  141
  Minor opcode:  14
  Resource id:  0x1d5
2007-01-11 05:48:03.470 TV: Changing from None to WatchingLiveTV
2007-01-11 05:48:03.475 New DB connection, total: 3
2007-01-11 05:48:03.486 Connected to database 'mythconverg' at host: localhost
2007-01-11 05:48:03.487 Using realtime priority.
2007-01-11 05:48:03.614 Video timing method: USleep with busy wait



---

### Post by majoridiot on 2007-01-11
the error you highlighted is a known error and unrelated...

you might try looking at the picture adjustments for the record and playback options, to see
if the hue, etc. is off.  press G in livetv for record, F for playback.  the arrow keys adjust the
settings... i suggest making sure all are set to 0 to begin with.

---

### Post by Green_Star on 2007-01-11
Is there any easy way to reset all my mythtv video play back settings to default? Like deleting any configuration file ...etc?

---

### Post by majoridiot on 2007-01-11
you can reset them manually, as described above or by finding and editing each entry in the
mythconverg database.  unfortunately, all of the config settings are stored in the database, so
it's not as simple as pulling up and poking around a conf file.

if you want to just start from scratch (settings-wise, not installation-wise), you can just drop
the entire database, reload the initial tables, etc. and go from there.  if you do, you will need to
configure EVERYTHING again... cards, tuners, running mythfilldatabase, etc.

i'd try adjusting the record and playback settings first, if it were me.

---

### Post by Green_Star on 2007-01-12
Thanks majoridiot,

I guess my problem is with some thing to do with my ATI card, pvr-150 and mythtv. Because i just configured my mythtv, so i do not think i changed my video play back settings. but still i am gonna try as you suggested.

---

### Post by herpes on 2007-01-15
Broken I420 support in ATI's driver is the problem, see [https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/73102](https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/73102) - install the libmyth .deb that Brin kindly posted there, then do

```
echo 'libmyth-0.20 hold' | sudo dpkg --set-selections
```

to stop libmyth updating itself to the original. Ask ATI to fix their driver too - [http://support.ati.com/ics/survey/survey.asp?deptID=894&surveyID=508&type=web](http://support.ati.com/ics/survey/survey.asp?deptID=894&surveyID=508&type=web) - if enough people shout about it they may eventually fix it. ](*,)

---

### Post by peabody on 2007-01-15
I concur, I have an ati card and have experienced this problem.  ATI's drivers for linux have been the most crap piece of software I have ever had the misfortune of being required to deal with.  When I have the money to buy a new machine I am going with nVidia and am never looking back.

---

### Post by majoridiot on 2007-01-15
very good to know that this is an ATI problem so we can quit running in circles!  i absolutely
concur on the ATI opinions... when i first made the switch to linux, i fought ATI's ridiculous and
shoddy drivers for about a month, before yanking the card and installing nvidia units.

nvidia's drivers may be closed, but they have the best support and development going, atm.

---

### Post by peabody on 2007-01-15
> **majoridiot said:**
> 
nvidia's drivers may be closed, but they have the best support and development going, atm.

Did ATI's drivers ever get opened?  I heard rumors about AMD eventually opening up the drivers but I haven't been paying much attention in that realm.  Last I heard they were closed, which still puts ATI far below nVidia in my mind.  Like you said, at least nVidia provides quality.

---

