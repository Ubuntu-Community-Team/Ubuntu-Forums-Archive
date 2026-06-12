---
title: "rtmpdump help required"
date: 2015-01-07
forum: General Help
---

### Post by lidra on 2015-01-07
Hi Guys, 

I need some help with rtmpdump utility. 
I use an IPTV provider that creates a list of its channels for XBMC playing (Livestream). 
I am trying to access the streams outside XBMC, but without much luck. 

What I need is for somebody with experience in rtmpdump commands to translate how to use one of the streams. 
Here is how a stream info comes in provide list:

<item>
<title>TVR 1</title>
<link>rtmp://cdn1.us.spicetvnetwork.zone:1935/live?c=5&amp;u=66302&amp;e=1420619579&amp;t=56877e65b09a0d8a4b80ca4a22ba9307&amp;d=xbmc&amp;i=84307 playpath=mp4:spicetv/ro/TVR1.stream swfUrl=http://static.spicetvbox.com/flash/jwplayer.flash.swf pageUrl="http://api.spicetvbox.com/live/tvr-1" swfVfy=true live=true</link>
<thumbnail>http://www.spicetvbox.com/storage/channels/tvr-1.png</thumbnail>
<epg></epg>
</item>

I manage to get this far:

rtmpdump -r "rtmp://cdn1.us.spicetvnetwork.zone:1935/live?c=5&u=66302&e=1420619579&t=56877e65b09a0d8a4b80ca4a22ba9307&d=xbmc&i=84307" -a "live/" -f "LNX 11,6,602,171" -W "http://static.spicetvbox.com/flash/jwplayer.flash.swf" -p "http://api.spicetvbox.com/live/tvr-1" -y "nnnnnn.sdp" -o nnnnnn.flv

But I get the following error "ERROR: Closing connection: NetStream.Play.Failed" . 

Please note you will not be able to access the stream yourself as it is locked on each user's IP. 
I am trying this on 14.04 fresh install and fully updated. 

Best Regards, 

Liviu

---

