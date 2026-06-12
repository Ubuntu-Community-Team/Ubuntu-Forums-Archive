---
title: "RealPlayer 10 SUCKS!!!!"
date: 2005-07-07
forum: General Help
---

### Post by ephman on 2005-07-07
i have been trying to play this link below using realplayer 10.  on my wife's winxp machine no problemo, but on my linux box it starts at 225kbps, but then after about 20 seconds it slows right down to 20kbps.  it's unbearable.  is there anyohter apps that can play .ram files?  has anybody else had this issue with this player?

[http://www.cbc.ca/clips/national/thenational.ram](http://www.cbc.ca/clips/national/thenational.ram)

thanks,
ephman

---

### Post by bunced on 2005-07-07
Real player should be the only one that can play .ram files. You could try Totem Movie Player with Win32 codecs though!

David

---

### Post by celloandy on 2005-07-08
I've actually had good luck with RP 10, but if you don't like it, the win32 codec package in the Marillat repository includes Real codecs, so any movie player that supports those will work.  That would include anything based on mplayer (like the mplayer mozilla plugin, which is what I used before I installed RP 10), or xine (like xine-ui or totem-xine), and now, GStreamer (so, totem-gstreamer), using the PitfDLL GStreamer filter, though this doesn't seem to be in either the Ubuntu or Marillat repositories.  mplayer-plugin may be your best bet for now.  Best of luck!

Andrew

---

### Post by angkor on 2005-07-08
No problems here with Realplayer 10 watching the .ram you linked to.

How did you install Realplayer? Did you use the Ubuntu installer or did you install it yourself from the realplayer website?

---

### Post by yanik on 2005-07-08
I clicked on the link and totem played it, I have w32codecs and totem-xine installed

---

### Post by darkaudit on 2005-07-08
I try to view this link in RP 10: [http://www.reelradio.com/ram/beg2.ram?kbox112263.rm~0:00.0~06:48.2](http://www.reelradio.com/ram/beg2.ram?kbox112263.rm~0:00.0~06:48.2)

And the player will crash in the middle of playing. Or immediately if I try to skim through the track. Happened in every version of RP 10 I've tried.

---

### Post by yanik on 2005-07-08
And also, Radio One and Radio Two (as well as their french counterparts) broadcast in ogg vorbis, this is great!

CBC Radio One:[http://www.cbc.ca/livemedia/cbcr1-toronto.m3u](http://www.cbc.ca/livemedia/cbcr1-toronto.m3u)
CBC Radio Two:[http://www.cbc.ca/livemedia/cbcr2-toronto.m3u](http://www.cbc.ca/livemedia/cbcr2-toronto.m3u)
RC Première Chaine:[http://ms2.radio-canada.ca/PremiereChaine.ogg.m3u](http://ms2.radio-canada.ca/PremiereChaine.ogg.m3u)
RC Espace Musique:[http://ms2.radio-canada.ca/EspaceMusique.ogg.m3u](http://ms2.radio-canada.ca/EspaceMusique.ogg.m3u)

---

### Post by manicka on 2005-07-08
No problems playing it here. Looks to me like it's supposed to play at about 20kb/s.

---

### Post by mtron on 2005-07-08
Well, If this is the streaming media thread: 

BBC Streams: 
http://support.bbc.co.uk/multicast/rams/uni/bbc1.ram (seems to be only during GMT daytime)
http://support.bbc.co.uk/multicast/rams/uni/bbc2.ram (seems to be only during GMT daytime)
http://support.bbc.co.uk/multicast/rams/uni/video16.ram (after 7 pm)
http://support.bbc.co.uk/multicast/rams/uni/news24.ram (24 hours)

and for german speaking people out there: 
http://rstreaming.zdf.de/encoder/3sat_h.ram (3sat culture & arts, 24 hours)
rtsp://real.ntv.t-bn.de/live/ntv/ntv_1.rm (N-tv.. german CNN, 24 hours)
rtsp://rd01.t-bn.de/live/viva/viva1tv_live_adsl.rm (VIVA music channel, 24 hours)
http://www.wdr.de/wdrlive/media/wdrfs-gross.ram (WDR, only evenings)
http://rstreaming.zdf.de/encoder/phoenix_h.ram (Phoenix Event channel, 24 hours)
rtsp://a141.l1434039337.c14340.g.lr.akamaistream.net/live/D/141/14340/v0001/reflector:39337 (Deutsche Welle TV, 24 hours)

Burn your television  :wink:

---

### Post by ephman on 2005-07-14
ok well my cbc broadcast is now working properly.  it had to be on cbc's end.  i'm back up to 225kbs

thanks,
ephman

---

