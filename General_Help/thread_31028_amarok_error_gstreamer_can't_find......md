---
title: "amarok error gstreamer can't find....."
date: 2005-05-01
forum: General Help
---

### Post by deet on 2005-05-01
Amarok worked for a while but ive always had to change the settings from esd to something else and then back to get any sound at all.  Then it used to work

now I get the error gstreamer error could not open connection to esound server.

in my experience ubuntu has been really difficult to get the sound working at all.

has anyone else had this problem or have any ideas.

how is the sound set up in ubuntu anyway? waht is esd oss alsa gstreamer

why so many options and possibilities for conflicts

Thanks 
Fred

---

### Post by Nis on 2005-05-03
The sound situation in Linux is pretty complicated but it is getting better.  ALSA is the sound infrastructure used by most Linux distributions now.  
1) Drivers and such things that interface directly to the soundcard are here.  OSS was the old way to do this but now ALSA leads the way and has an OSS wrapper to inteface with older applications.
2) esd is a sound server that allows applications to do software mixing.  Software mixing allows multiple sounds to play at once but it is slower than hardware mixing.  If you can, get a cheap card that does hardware mixing and things are much better.  Check [here](http://www.alsa-project.org/alsa-doc/index.php?vendor=All) to find a card that does hardware mixing.  esd sits on top of ALSA.
3) gstreamer is a multimedia framework (a way to present audio and video).  It uses esd to work (or ALSA directly if you have hardware mixing).  Applications that use gstreamer then do not have to worry if someone is using esd or not (unless gstreamer is setup to use esd).

If you're using Kubuntu I would suggest installing artsd support for gstreamer (search for artsd in Kynaptic).  If you're using Ubuntu start esd with the command below:
```

esd --nobeeps &

```
Make sure System/Preferences/Sound has a check next to starting the sound server.

---

