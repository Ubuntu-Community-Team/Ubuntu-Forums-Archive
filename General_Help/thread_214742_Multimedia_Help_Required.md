---
title: "Multimedia Help Required"
date: 2006-07-13
forum: General Help
---

### Post by greengrocer on 2006-07-13
Hello All,

I am having considerable trouble with getting Ubuntu 5.10 Breezy Badger to provide a rich Multimedia experience for the user.

I have the following Multimedia capable applications installed:

Totem-xine
Xine
MPlayer
XMMS

I have the following codec packs and libs installed:

sox
Win32codecs
libdvdcss2
gstreamer0.8-plugins

I also have a folder /usr/lib/win32 which has a bunch of DLL's etc which were unipped from a file I downloaded following a how-to I read. They came from a file called "essential<yada yada>20060611.tar.gz

The following are my observations:

1) Xine will play DVD but playback tends to jitter and jump a bit unless I use the command "hdparm -d1 -c1 /dev/dvd" before running Xine. The command "hdparm -d1 -c1 /dev/dvd" cleans up the jitter and jumps and playback becomes 100% perfect.

2) Xine does not play AVI's well, the audio and video are out of sync. Video is smooth though.

3) MPlayer does not play AVI's well, the video is jittery but the audio is in Sync.

4) Mplayer does not play DVD's well at all. Everything is jittery.

5) XMMS plays back MP3 perfectly.

6) Totem-xine performs nearly the same as Xine itself (as expected) except that Xine demonstrates better stability when it comes to the user sliding the position bar up and down.

WMV playback quality tends to differ between the Multimedia apps.

7) Xine will play back a WMV file with the video smooth, but audio virtually non-existant aside from a few random "bleeps" here and there.

8) MPlayer will play back a WMV file with audio more or less in tact but everything stops and starts like someone is clicking play...pause...play...pause..play...pause....play.



Does anybody know of any tricks to improve this situation? As it stands, this multimedia experience is very week and needs a lot of work. If this is the average user experience for Multimedia, then it is no wonder a majority of people stick to Windows, where on Windows the Multimedia experience is rich and people can share all sorts of content amongst each other without nearly as many issues.

I am not supporting Windows in any way, I myself prefer Linux and put up with a lot of the crap, but if we want to encourage people to migrate, we need to offer the same or better experience to the end user as what Windows can acheive.

Regards,
Greenie

---

### Post by encompass on 2006-07-13
what is your graphics card?  Could be your using vesa and it just isn't cutting it.

---

### Post by sagibson on 2006-07-13
For the DVD you may want to be sure that DMA is on
 
[https://help.ubuntu.com/community/DMA](https://help.ubuntu.com/community/DMA)

---

### Post by greengrocer on 2006-07-13
Graphics card is an Nvidia 6200 Turbo Cache.

I had the Nvidia drivers installed, but I have since ditched them because the Nvidia drivers caused holes to appear in Google Earth.

It also made Google Earth mix up its maps, so Hoover Dam appeared in France,  someones house appeared where the Pyramids of Egypt should be, and Antartica was covering Ayres Rock in Australia.

When I uninstalled the driver, Google Earth returned to OpenGL mode and everything returned to normal (except that it is a bit sluggish in OpenGL mode).


@ sagibson - Yep, I switch the DMA to the DVD Rom on with the command 'hdparm -d1 -c1 /dev/dvd'  Do you think I need to do the same to the hard disk in order to play files that are stored on the hard disk?

---

### Post by greengrocer on 2006-07-13
Well I managed to get Mplayer to work well with .ASF, .WMV and .AVI files by doing the following:

1) Creating the dir /usr/local/lib/codecs
2) unpacking and copying the Mplayer essential codec pack to /usr/local/lib/codecs
3) Setting the audio device in the configuration menu (gui) to ESD (changed from ALSA to ESD) That is ALSA causing the problem.

So now I have quite reasonable Multimedia functionality, I can now play the following media types (listed by best performing player for that type):

ASF - Mplayer
WMV - Mplayer
AVI - MPlayer
MPG - MPlayer
MP3 - Rhythmbox, XMMS
DVD - Xine
Internet Radio (shoutcast) - Rhythmbox

---

