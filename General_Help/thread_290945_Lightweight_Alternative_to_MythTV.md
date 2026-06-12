---
title: "Lightweight Alternative to MythTV"
date: 2006-11-01
forum: General Help
---

### Post by BarfBag on 2006-11-01
I don't have any type of premium television whatsoever.  Just use the free, over-the-air, local channels.  I'm obviously not hardcore enough to build a dedicated MythTV box.  I'm looking for a program as lightweight as possible (that runs in the background) that'll record things for me.  Any ideas?

---

### Post by John.Michael.Kane on 2006-11-01
Have you tried tvtime?
It should be in the repo's.

[http://tvtime.sourceforge.net/](http://tvtime.sourceforge.net/)

---

### Post by Naegling23 on 2006-11-01
tvtime does not record.  If you want tivo, the only thing I can recommend is mythtv.  The good news is that the install of myth0.20 on edgy was dare I say....easy.  You dont need to dedicate your box to mythtv, I just load it up off of my regular user account when I want to record tv, and it does record in the background.

---

### Post by reclusivemonkey on 2006-11-02
> **BarfBag said:**
> I don't have any type of premium television whatsoever.  Just use the free, over-the-air, local channels.  I'm obviously not hardcore enough to build a dedicated MythTV box.  I'm looking for a program as lightweight as possible (that runs in the background) that'll record things for me.  Any ideas?

[http://ubuntuforums.org/showpost.php?p=1665786&postcount=7](http://ubuntuforums.org/showpost.php?p=1665786&postcount=7)

---

### Post by patrick295767 on 2006-11-10
xawtv records

ttoo:
> What is GShow TV?

GShow TV is a TV program schedule viewer and a Personal Video Recorder GUI. GShow TV's basic purpose is to provide a nice GUI for viewing tv program schedule information and for recording the programs. GShow TV doesn't itself do the recording of the selected programs, rather it uses any PVR solution that exists. GShow TV is globally usable as it uses XMLTV to access the program schedules, and xmltv has support for multitude of countries. (early 2006 support for Australia, Belgium, Brazil, Canada, Denmark, Estonia, Finland, France, Germany, Hungary, Iceland, Italy, Japan, Norway, Portugal, Reunion Island, Romania, Russia, South Africa, Spain, Spain, Sweden, Switzerland, The Netherlands, The UK, The USA and more.) 
  
  
> Zapping is a TV viewer for the Gnome desktop. It runs on Linux Icon Linux, FreeBSD Icon FreeBSD and Solaris.

With Zapping and a TV card you can watch TV, take screenshots, and record video and audio. Zapping has a deinterlacer and a Teletext viewer built in and supports Closed Caption and Teletext subtitles. Got a remote control? Zapping supports LIRC too

---

### Post by Lem on 2006-11-10
You can run mythtv on a desktop ubuntu build quite easily. In fact it works so well i've swopped my knoppmyth box over to ubuntu.

This guide is pretty good; [http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)

I had to insert modules in /etc/modules to get my twinham dvb cards to recognise but other that that it was fine.

Mythbackend sits in the background and will record away while you work. You can fire up Mythfrontend from the menu when you want to watch something, set a recording or change a setting. 
Spend a little time setting up Mythweb and you can schedule stuff over the web stuff - very cool.

---

### Post by aum11 on 2006-11-19
Am successfully using Kaffeine to record tv and also to timeshift.  Very easy to set up.

---

### Post by charlesw on 2006-11-24
heres the way i do it and its not super automated but i can  record things so it works for me ..and this is about as light weight as you can get that im aware of 

1.) install xawtv and streamer and all the multimedia codecs (for example all the gstreamer stuff and w32codecs) info for the codecs is all on the ubunutu guide page. 

2) make this a vcr script code:
#!/bin/bash
streamer -p 4 -t 60:00 -r 24 -q -o test.avi -j 90 -f mjpeg -F stereo
#use chmod u+x or something to make ./vcr executable
if you change the 60:00 to 120:00 itll record 2 hours for example.. 

that will record avi files then to convert to mpeg video

3)make this avi2mpeg script:
ffmpeg -i test.avi -y -f vcd -vcodec mpeg1video -map 0.0:0.0 -b 1150 -s 352x240 -r 29.97 -g 12 -qmin 3 -qmax 13 -acodec mp2 -ab 224 -ar 44100 -ac 2 -map 0.1:0.1 test.mpg

then rename it to whatever it is and drop it in your movies/tv shows whatever folder.  

you can look around for how to setup a cron job to automate it or whatever but i usually just type ./vcr in a terminal when i know i want to record something and come back to it later when its done.. yes its ugly and not as "1337" as mythtv or freevo but it works and i can record movies and shows without install a ton of stuff i dont like.. some suggested apps might be totem with all the plugins and xine and avidemux (to edit out commercials its simple to use) 

hope it helps .. im running on a p3 1ghz with 512 ram and a 80 gb drive  an hour of recoring to avi is roughly 1gb before converting to mpeg video.

hope it helps you out charlesw.

---

