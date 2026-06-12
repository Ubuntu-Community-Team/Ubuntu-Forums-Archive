---
title: "Garmin GPS navis and Ubuntu"
date: 2014-11-06
forum: General Help
---

### Post by andrew_s4 on 2014-11-06
I'm running only 14.04 Ubuntu, after getting rid of windows. What I didn't calculate were the map updates from Garmin. Garmin only offers the map updates for windows and mac. I've written to Garmin for support, but no reply yet. Anyone know how to go about getting Garmin GPS updates to download and work. I have a Garmin Nuvi 2595LM.

---

### Post by ian-weisser on 2014-11-06
Some Garmin devices can be updated by applications in the Software Center. Search for 'Garmin'
Some cannot.

Garmin is long aware that they don't support Linux.

---

### Post by HermanAB on 2014-11-06
Easy.  Abandon Garmin and use OpenStreetmap.

[http://garmin.openstreetmap.nl/](http://garmin.openstreetmap.nl/)

The default name is gmapsupp.img and it MUST reside in a directory \Garmin on the SD card.  The card must be formatted with FAT32 (type cH).

These maps can be renamed to something else on some newer Garmins provided that the name ends with .img e.g.: german.img - this doesn't work on a Nuvi 1310, so YMMV.

I put a large number of maps on a SD card and copy them to gmapsupp.img using a laptop machine as needed.

---

### Post by ajgreeny on 2014-11-06
> **HermanAB said:**
> Easy.  Abandon Garmin and use OpenStreetmap.

[http://garmin.openstreetmap.nl/](http://garmin.openstreetmap.nl/)

The default name is gmapsupp.img and it MUST reside in a directory \Garmin on the SD card.  The card must be formatted with FAT32 (type cH).

These maps can be renamed to something else on some newer Garmins provided that the name ends with .img e.g.: german.img - this doesn't work on a Nuvi 1310, so YMMV.

I put a large number of maps on a SD card and copy them to gmapsupp.img using a laptop machine as needed.
You make that sound extremely easy, but if Garmin satnavs are similar to TomTom it will not help, as my TomTom will not mount or show in Ubuntu, so there is no way to copy anything to it

 The only way I can update my TomTom is with a VM of WinXP in VBox, which I installed specifically for this purpose, where everything works well, or as well as it can using Windows.

Perhaps Garmin work very differently from TomTom.  I wish you a lot of luck; let us all know how you get on.

---

### Post by rbmorse on 2014-11-06
Had to do the same thing here using a VMWare Workstation VM.

---

### Post by andrew_s4 on 2014-11-07
Very interesting! Well, Garmin mounts as does the SD card in it in Ubuntu. So as soon as the map from [http://garmin.openstreetmap.nl/](http://garmin.openstreetmap.nl/) is ready for me I'll see what happens. Fortunately I have an older Garmin nuvi 1390 which I'll try it out on. There are lots of features which come with the original garman maps, and I'll be interested to see how many of these will work with the free maps. 
Will update...

---

### Post by andrew_s4 on 2014-11-07
The problem I have with the above system, is I'm not sure if the satnav is using the maps I just installed under /Garmin on the SD card, or if it is just using the old ones. There is nothing to tell me which file or set of maps is being used, and/or if the new unziped gmapsupp.img in /Garmin is just sitting there doing nothing.

---

