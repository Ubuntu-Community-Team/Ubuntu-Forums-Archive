---
title: "stream real player in live dvd dapper"
date: 2006-10-01
forum: General Help
---

### Post by jimjan on 2006-10-01
have dapper 6.06 on dvd and trying to stream internet stations like npr from live disk operation

what is easiest way to do htis
-rhythem box [smil files]
-real player 10 [get codecs]

have read the info below and its not clear the best way to go and not enough detail for a novice like myself to get step by step thru the process

suggestions about best path to stream radio stations that use real player stream and a detailed step by step on how to achieve in live cd/dvd os setup??

thanks

background info reviewed but not sure how to use--[do these instructions apply to live or hard drive os status?]

1-info found on forum

=Rhythmbox will play mp3s just fine.. just make sure you have the right codecs installed 
=To install the codecs, you have to enable the universe repositories and then in a terminal:
This will install all the gstreamer plugins including the one needed for mp3s: sudo apt-get install gstreamer0.8-plugins
For just the mp3 codec: sudo apt-get install gstreamer0.8-mad

2-info from formal forum page

Playing Streaming Video from the Internet [from restricted format page at ubuntu]

      Ubuntu

      There are a variety of plugins that allow you to play streaming video in your browser. The recommended plugin is totem-xine-firefox-plugin. First, install the Windows Codecs, then install the totem-plugin.

      On Ubuntu, Totem can use either the gstreamer (default) or xine multimedia frameworks. The plugin installation process depends on the framework you use. If you use totem-gstreamer (the version of Totem that uses the gstreamer back-end), install the totem-gstreamer-firefox-plugin package. If you use totem-xine, install the totem-xine-firefox-plugin package.

Real Media

      Following the instructions above should enable most media players (such as Totem and Kaffeine) to play RealMedia files, however some functionality such as resuming (after pausing or connection problems) or skipping through streaming files is not supported, so you may wish to set up Realplayer to be the default application to open RealMedia file types:

      Ubuntu

            Use the File Manager to navigate to a folder containing a sample RealMedia file. Click the file with the right mouse button, select Properties, and then the tab Open With. Click the radio button next to RealPlayer 10, and close the dialog window.

Smil

      If you want Realplayer to be the default application to open Smil file types:

      Ubuntu

            Use the File Manager to navigate to a folder containing a Smil file. Click the file with the right mouse button, select Properties, and then the tab Open With. Click the radio button next to RealPlayer10, and close the dialog window.


thanks again

---

