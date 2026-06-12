---
title: "Viking GPS manager"
date: 2008-05-17
forum: General Help
---

### Post by gewitty on 2008-05-17
Anybody out there using Viking GPS Manager? I have it installed and after a few initial set-up issues now have it working - almost.

The problem I have encountered is that when I download a stored track file from my Garmin Etrex, everything appears to work OK, but once the download has completed, there is no sign of the file and no display of the track.

I created a GPS layer and (according to the on-screen display)downloaded 243 trackpoints, but after doing this, nothing appears to have been captured.

The Viking Reference Manual is not very helpful on this subject. The only instruction given is, 'To download data from the GPS, right-click the GPSLayer and click "Download from GPS"'. Well, done that - what next?

If anyone has used Viking and knows a bit more about it than the manual explains, I would be very grateful to hear how this works.

---

### Post by kr00lplatinum on 2009-01-07
I can't get Viking GPS to download maps either. I'm using Ubuntu 8.10 and Viking GPS in the repos.  I did some searching and it looks like Google may have asked Viking developers to disable Google Map support.  I can't be absolutely sure though... 

Can I also can't get any of the Open Street maps working... possibly because they need Google support :confused:

---

### Post by fep1343 on 2009-01-12
Hi
I am running Viking Gps gps (0.9.6-2)under Ubuntu Hardy. It works great including map download & GPS Comminucation. For more information how to run a GPS & viking under Ubuntu see this web site:
[http://www.gpspassion.com/forumsen/topic.asp?TOPIC_ID=121878]("http://www.gpspassion.com/forumsen/topic.asp?TOPIC_ID=121878")

Verify that you have the latest version :Viking gps (0.9.6-2). If you install an older version, maps don't display.

---

### Post by SteinbergerNate on 2009-03-18
Yup. Make sure you have the latest. I often use the SVN to keep this one up to date. Also, make sure that you're over the area that your gps data is at. You should be able to go to View/Go to Location and put in the city that the gps data is in.

---

### Post by smellyoulater on 2009-04-20
I just started playing around with GPS and ubuntu today.

I have a Gisteq USB dongle (GR-110) and Jaunty RC1.  

Between GPSdrive, TangoGPS, and Viking,  Viking is my favorite.  

Well... it would be if it didn't crash every time  I started real time tracking.   Its so frustrating that everything else in the program works great, except for that.  When i click it it shows me position, freezes, then closes the program.

I'm not sure if this is vikings fault, jaunty's fault, the USB Dongles fault, or my fault.

i suspect that its my fault.  When setting up the GPS layer, it asks for a GPS protocol, with the choices of Garmin or Magellan.
No my gisteq is a cheap chinese GPS dongle (it works great with everything else).  I'm pretty sure that it uses NMEA as the protocol.  Does viking only work with garmin and magellan devices?  cause that would really bum me out.

Anyone know what's going on?  

Now I know google asked them to take the google maps out, but does anyone know how to put them back in?  I really want those, as I live in Seoul and openmaps doesn't have great detail.

---

### Post by USD on 2009-04-28
I can't get viking to work either. That tutorial is for Garmin devices only - and I don't think my SiRF III device is Garmin compatible. It says WAAS compatible and NMEA 0183 default protocol (I wasn't aware of Viking when I bought my usb GPS device, and at that time I thought SiRF III chipset would be the best option).

I'm guessing Google map download doesn't work because they disabled it in the program due to Google's (do not evil) ridiculous ToC. Anyway, I'm only given two options in Viking: Garmin or Megellan... Why don't they use GPSd?

Viking persists with a big cross hair and doesn't download any maps. It also seems to be the best program for any of this type of work... Any suggestions?

---

### Post by fep1343 on 2009-04-29
Hi
Viking version (0.9.6-2) is still available & works with google maps. You can download Viking package(0.9.6-2) here:

[http://packages.debian.org/lenny/viking](http://packages.debian.org/lenny/viking)

The version of "0.9.8" doesn't support Google maps any more.

---

### Post by USD on 2009-04-29
I didn't mean to be unclear, but that is the exact version that I have (installed via apt-get).

---

### Post by gerkin on 2009-07-29
I think I finally worked out the problem with not seeing the tracks even when you can see all the waypoints in the download layer:

I think it's because Viking handles everything as layers - 

if you have the map/background layer above the download layer it hides the trackpoints just move the appropriate layer higher or lower in the stack

highlight the layer then use the  up/down keys at the lower left of Viking



cheers.................gerkin

---

### Post by travisn000 on 2009-08-16
..Once you have your track layer on top, you can add multiple map layers, right click them, and change their alpha to make them more or less see through to see multiple layers at once

---

### Post by digitography on 2011-07-14
I have just downloaded this software and trying to get my head around it.

I use something similar in Windoze called GPSutils, which works fine but I would like a linux based app.

As of yet I have so far simply created a new layout, added a track waypoint layer, and tried to add waypoints. I can see the waypoints on the side panel, but they do not appear on the map area.

Also I have tried to download maps using the OSM option, and nothing happens.
On the face of it this looks like a great app, but it's just not working, could be me, not sure.

Any assistance appreciated.

---

