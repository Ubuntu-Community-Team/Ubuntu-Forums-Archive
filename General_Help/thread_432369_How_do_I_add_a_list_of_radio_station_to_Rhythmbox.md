---
title: "How do I add a list of radio station to Rhythmbox?"
date: 2007-05-03
forum: General Help
---

### Post by tc101 on 2007-05-03
How do I add a list of radio station to Rhythmbox?  I see how to add one at a time, but I would like to add a big directory of lots of stations.

---

### Post by benanzo on 2007-05-04
the radio station information is held in ${HOME}/.gnome2/rhythmbox/rhythmdb.xml

it uses standard xml formatting to give the information that it needs

```
  <entry type="iradio">
    <title>Virgin Radio Classic Rock</title>
    <genre>Rock</genre>
    <artist></artist>
    <album></album>
    <location>http://www.smgradio.com/core/audio/ogg/live.pls?service=vcbb</location>
    <date>0</date>
    <mimetype>application/octet-stream</mimetype>
    <mb-trackid></mb-trackid>
  </entry>
```


you can see here how it is formatted.  I am not sure that there is a way to mass add a list of stations from within rhythmbox.  It shouldn't be too hard to take a list of stations and urls and write a script to auto-format them in this way and then just add that to this file.

---

### Post by tc101 on 2007-05-04
Thanks for the info.  I think I will just add the ones I want by hand.  I will ask in music forums for recommendations of good stations.  I also might try adding real player for linux, which probably comes with a big list.

[http://www.real.com/linux/](http://www.real.com/linux/)

Thanks again for you help.  I am new to linux and it is fascinating to see how much control we have over our system.

---

### Post by tc101 on 2007-05-04
I added "Listen Music Player" and it has hundreds of web radio stations already added.  Click the shoutcast tab to get them, then when you find the best ones right click and add them to favorites.

You can add  "Listen Music Player" from Applications/Add Remove

It is the best thing I have found in linux for web radio

---

### Post by benanzo on 2007-05-04
you might also have a look at banshee.  It is available in Add/Remove also.  It does Radio, Podcasts, iTunes Shares, etc.  There is a mountain of plugins available you can activate such as Wikipedia lookup, lyrics, last.fm  etc.

---

### Post by tc101 on 2007-05-04
I have found lots of sites that let you play from a huge list of radio stations, but I have not found any that give the actual address of the station.  For example this is the address of NPR:

mms://a1671.l2063252432.c20632.g.lm.akamaistream.net/D/1671/20632/v0001/reflector:52432?=C3657BAADBA0B724&=

But I had to go to the NPR site to get it.  I want to be able to copy and paste these addresses from a big list.

---

### Post by makbot on 2008-04-14
> **tc101 said:**
> I added "Listen Music Player" and it has hundreds of web radio stations already added.  Click the shoutcast tab to get them, then when you find the best ones right click and add them to favorites.

You can add  "Listen Music Player" from Applications/Add Remove

It is the best thing I have found in linux for web radio

++++

Hey Everyone 
I'm a new Linux user too! I cannot seem to search for any new stations or find the Listen Music Player in Add/Remove. Also, how do I install programs, they download as zipped files??

Many thanks...



Long live Linux!  :P

---

### Post by Ripfox on 2008-05-11
You need to enable extra repos...I think. Go to system/administration/software sources and check the boxes to add the extra repos then reload, you should have more available through add/remove then.

---

