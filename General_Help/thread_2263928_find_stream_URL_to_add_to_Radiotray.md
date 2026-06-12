---
title: "find stream URL to add to Radiotray"
date: 2015-02-04
forum: General Help
---

### Post by raspatan on 2015-02-04
Hello there. I use Radiotray to manage my radio streams and so far I have been able to find all URLs of online streams. I find them by looking at the page source on my browser. However, I just can't find the URL for this radio: 

[http://nowplaying.mediastre.am/station/51f7c25031675bae46000005](http://nowplaying.mediastre.am/station/51f7c25031675bae46000005)  

This radio is embedded in this website: radio.musicachilena.cl (from where I got the above link).

I don't know HTML language so I'm kind of lost among all that information. Any help is much appreciated!

---

### Post by ajgreeny on 2015-02-04
I can't even get it to play direct from that website, so the chance of getting radiotray to play it seems very limited.

---

### Post by PaulW2U on 2015-02-04
The audio plays perfectly here but if you look at the page's source code you'll see a link to download Flash Player from Adobe. Presumably Flash is used to play the audio and the link is there in case Flash Player is not already installed? Not something that Radio Player can deal with. 

I might be wrong, some of that HTML is a mystery. :confused:

---

### Post by Erik1984 on 2015-02-04
The ID of the station is in the URL, I found another URL for that ID through Google: [http://radio-cl.origin.mdstrm.com:8000/51f7c25031675bae46000005.mp3](http://radio-cl.origin.mdstrm.com:8000/51f7c25031675bae46000005.mp3) This should work in RadioTray although It wasn't a steady stream for me.

---

