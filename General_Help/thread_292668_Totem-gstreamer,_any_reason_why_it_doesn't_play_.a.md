---
title: "Totem-gstreamer, any reason why it doesn't play .asx files?"
date: 2006-11-04
forum: General Help
---

### Post by speedsix on 2006-11-04
It plays pretty much everything I've found except asx, any ideas? I know xine does but I'd rather stick to one player.


Thanks

---

### Post by PuleX on 2006-11-04
I did a quick search. ASX is just a [file redirecting to]("http://filext.com/detaillist.php?extdetail=ASX") a ASF streaming file, if I understand it correctly. 

It seems that quite some people have had problems with it (forum search: "ASX"): 
 - this guy hasn't been able to play asx with the totem plugin either: [http://ubuntuforums.org/showthread.php?t=285261&highlight=asx](http://ubuntuforums.org/showthread.php?t=285261&highlight=asx) 
 - a kaffeine user (xine backend) couldn't make it work either: [http://ubuntuforums.org/showthread.php?t=253514&highlight=asx](http://ubuntuforums.org/showthread.php?t=253514&highlight=asx) 

There's another thread from a yeag ago about a similar problem: [http://ubuntuforums.org/showthread.php?t=71164&highlight=asx](http://ubuntuforums.org/showthread.php?t=71164&highlight=asx) 
Thing is, I've tried the url's from that thread and the radio link  mms://rdp.oninet.pt/antena1 works for me in totem gstreamer. The video link to [http://byutv.org/streaming/byutv250b.asx](http://byutv.org/streaming/byutv250b.asx) also opens in the totem plugin, and loads a black and white image, but doesn't play a video file. 

I know this doesn't really help, but it's a start. What ASX files were you trying to play?

---

### Post by PriceChild on 2006-11-04
I stream Kerrang Radio... the best radio station ever ;)

I got it all working by first adding the stream to vlc.

From there, i managed to dissect the stream to all the different files,
finding the asx file's location which i could easily add to any media player i wanted :)

---

### Post by speedsix on 2006-11-04
Hi,

This is the file
[http://www.bbc.co.uk/radio2/wm_asx/aod/radio2_hi.asx](http://www.bbc.co.uk/radio2/wm_asx/aod/radio2_hi.asx)


It will play in Xine but I just wondered why Totem-gstreamer doesn't play it (all plugins installed) seeing as it is after all the default Ubuntu media player.



Dom

---

### Post by PuleX on 2006-11-04
Just so you know, the release notes for [Totem 2.16.2 on the gnomefiles.org]("http://www.gnomefiles.org/app.php?soft_id=64") site mention an improvement: 
>  - Handle "BASE HREF" in ASX files 

So they have been working on it. 
If you cannot fix it, do report an extensive bug report: 
[https://launchpad.net/distros/ubuntu/+source/totem/+bugs](https://launchpad.net/distros/ubuntu/+source/totem/+bugs)

---

### Post by PuleX on 2006-11-04
That url doesn't work for me either.  :( 

The asxfile looks like this: 
```
<ASX version="3.0">
   <ABSTRACT>http://www.bbc.co.uk/radio2/</ABSTRACT>
   <TITLE>BBC</TITLE>
   <AUTHOR>BBC</AUTHOR>
   <COPYRIGHT>(c) British Broadcasting Corporation</COPYRIGHT>
   <MoreInfo href="http://www.bbc.co.uk/radio2" />
   <Entry>
        <ref href="mms://wmlivegeo.bbc.net.uk/wms/radio2/radio2_nb_e1s1" />
        <ref href="mms://wmlivegeo.bbc.net.uk/wms/radio2/radio2_nb_e1s2" />
        <ref href="mms://wmlivegeo.bbc.net.uk/wms/radio2/radio2_nb_e2s1" />
        <ref href="mms://wmlivegeo.bbc.net.uk/wms/radio2/radio2_nb_e2s2" />
          <MoreInfo href ="http://www.bbc.co.uk/radio2/" />
          <Abstract>BBC Radio 2</Abstract>
   </Entry>
</ASX>
``` 

Opening the first url mentioned in there also doesn't work in standalone Totem (gstreamer off course).

---

