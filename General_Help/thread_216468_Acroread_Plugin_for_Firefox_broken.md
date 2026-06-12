---
title: "Acroread Plugin for Firefox broken"
date: 2006-07-15
forum: General Help
---

### Post by matthias_k on 2006-07-15
Hi,

it seems to me that the mozilla-acroread package shipping with Dapper is broken. It installs the plugin and sets the symbolic link in /usr/lib/firefox/plugins correctly, but still Firefox doesn't mention it in about:plugins.

As if this wouldn't be weird enough, when I install acroread from the seveas repo, the plugin suddenly gets recognized by Firefox, but still fails to work, in that it reports an error when I want to display a PDF in Firefox ("Plugin ewh.api failed to initialize"). This is probably because only the acroread package in Seveas gets maintained, they don't have an accompanying mozilla-acroread package which matches their acroread version.

Did anyone else notice this?

---

### Post by Perfect Storm on 2006-07-15
Did you install:

acroread
mozilla-acroread
acroread-plugins

If so, try comment Sevears in your sourcelist and try with the multiverse one.

---

### Post by matthias_k on 2006-07-15
> **Artificial Intelligence said:**
> Did you install:

acroread
mozilla-acroread
acroread-plugins
Well, I installed the former two. Why should I install acroread-plugins?

---

### Post by Perfect Storm on 2006-07-15
It's to your browser.

---

### Post by matthias_k on 2006-07-15
> **Artificial Intelligence said:**
> It's to your browser.
Hm? acroread-plugins has nothing to do with displaying PDFs in Firefox...

---

### Post by matthias_k on 2006-07-15
> **Artificial Intelligence said:**
> Did you install:
If so, try comment Sevears in your sourcelist and try with the multiverse one.
I installed from multiverse, it doesn't work.

---

### Post by Perfect Storm on 2006-07-15
Sorry, for the wrong information (I'm doing a billion stuff at the same time).

Try with symblink to mozilla-firefox

---

### Post by matthias_k on 2006-07-15
> **Artificial Intelligence said:**
> 
Try with symblink to mozilla-firefox

/usr/lib/mozilla-firefox is a symlink to /usr/lib/firefox

The content of these two directories are identical.

---

### Post by Perfect Storm on 2006-07-15
Strange....

Did you update to the latest kernel? I've seen reports of strange things with the latest kernel on this board.

---

### Post by matthias_k on 2006-07-15
Yes I did, but I doubt it's a kernel problem. It was like this since day 1, even after a clean install.

---

### Post by Perfect Storm on 2006-07-15
Have you seen if it's only a firefox thing or does it occure with other browsers as well?

---

### Post by matthias_k on 2006-07-15
Hmm, it works in the Mozilla Suite! Odd... It seems to be Firefox-specific then.

They use the same plugin:
```

matthias:plugins$ pwd && ll | grep nppdf
/usr/lib/firefox/plugins
lrwxrwxrwx 1 root root   50 2006-07-15 20:28 nppdf.so -> ../../Adobe/Acrobat7.0/Browser/intellinux/nppdf.so

```

```

matthias:plugins$ pwd && ll | grep nppdf
/usr/lib/mozilla/plugins
lrwxrwxrwx 1 root root     50 2006-07-15 20:28 nppdf.so -> ../../Adobe/Acrobat7.0/Browser/intellinux/nppdf.so

```
Both point to the same file.

---

### Post by Perfect Storm on 2006-07-15
Just for the heck of it ;)
remove purge firefox and its locale setting in your home folder, and do a clean install of firefox.
It could be the firefox was/is somehow damage on your Ubuntu CD (who knows).

Personally I don'y use firefox, but it's my guess.

---

### Post by matthias_k on 2006-07-20
Still not working.

Can someone please post his pluginreg.dat file in ~/.mozilla/firefox ?
I noticed that it's missing the entry for the plugin. However, copying the entry over from MozillaSuite's pluginreg.dat only had the effect that the plugin is now listed in about:plugins, but it still doesn't work (clicking a PDF will just open en empty page).

---

### Post by edemark on 2006-07-27
OK I have the same problem with my acrobat reader.

Here I have find an answer 
[http://www.ubuntuforums.org/showpost.php?p=832057&postcount=424](http://www.ubuntuforums.org/showpost.php?p=832057&postcount=424)

just in case you still having this problem

---

### Post by experiment437 on 2006-08-04
> **edemark said:**
> OK I have the same problem with my acrobat reader.

Here I have find an answer 
[http://www.ubuntuforums.org/showpost.php?p=832057&postcount=424](http://www.ubuntuforums.org/showpost.php?p=832057&postcount=424)

just in case you still having this problem

that's not the answer, i already did that and i'm having the same problem as matthias_k.

---

### Post by 8oluf7 on 2006-08-05
> **matthias_k said:**
> Still not working.

Can someone please post his pluginreg.dat file in ~/.mozilla/firefox ?
I noticed that it's missing the entry for the plugin. However, copying the entry over from MozillaSuite's pluginreg.dat only had the effect that the plugin is now listed in about:plugins, but it still doesn't work (clicking a PDF will just open en empty page).

This is mine on an AMD64 machine running the K7 kernel:

```
Generated File. Do not edit.

[HEADER]
Version:0.08:$

[PLUGINS]
/usr/lib/j2re1.5-sun/plugin/i386/ns7/libjavaplugin_oji.so:$
:$
1125104384000:1:5:$
Java(TM) Plug-in 1.5.0_05:$
Java(TM) Plug-in 1.5.0_05-b05:$
31
0:application/x-java-vm:Java::$
1:application/x-java-applet:Java::$
2:application/x-java-applet;version=1.1:Java::$
3:application/x-java-applet;version=1.1.1:Java::$
4:application/x-java-applet;version=1.1.2:Java::$
5:application/x-java-applet;version=1.1.3:Java::$
6:application/x-java-applet;version=1.2:Java::$
7:application/x-java-applet;version=1.2.1:Java::$
8:application/x-java-applet;version=1.2.2:Java::$
9:application/x-java-applet;version=1.3:Java::$
10:application/x-java-applet;version=1.3.1:Java::$
11:application/x-java-applet;version=1.4:Java::$
12:application/x-java-applet;version=1.4.1:Java::$
13:application/x-java-applet;version=1.4.2:Java::$
14:application/x-java-applet;version=1.5:Java::$
15:application/x-java-applet;jpi-version=1.5.0_05:Java::$
16:application/x-java-bean:Java::$
17:application/x-java-bean;version=1.1:Java::$
18:application/x-java-bean;version=1.1.1:Java::$
19:application/x-java-bean;version=1.1.2:Java::$
20:application/x-java-bean;version=1.1.3:Java::$
21:application/x-java-bean;version=1.2:Java::$
22:application/x-java-bean;version=1.2.1:Java::$
23:application/x-java-bean;version=1.2.2:Java::$
24:application/x-java-bean;version=1.3:Java::$
25:application/x-java-bean;version=1.3.1:Java::$
26:application/x-java-bean;version=1.4:Java::$
27:application/x-java-bean;version=1.4.1:Java::$
28:application/x-java-bean;version=1.4.2:Java::$
29:application/x-java-bean;version=1.5:Java::$
30:application/x-java-bean;jpi-version=1.5.0_05:Java::$
/opt/firefox/plugins/libnullplugin.so:$
:$
1138971411000:1:5:$
The default plugin handles plugin data for mimetypes and extensions that are not specified and facilitates downloading of new plugins.:$
Default Plugin:$
1
0:*:All types:.*:$
/opt/firefox/plugins/nppdf.so:$
:$
1138971412000:1:5:$
The Adobe Reader plugin is used to enable viewing of PDF and FDF files from within the browser.:$
Adobe Reader 7.0:$
5
0:application/pdf:Portable Document Format:pdf:$
1:application/vnd.fdf:Acrobat Forms Data Format:fdf:$
2:application/vnd.adobe.xfdf:XML Version of Acrobat Forms Data Format:xfdf:$
3:application/vnd.adobe.xdp+xml:Acrobat XML Data Package:xdp:$
4:application/vnd.adobe.xfd+xml:Adobe FormFlow99 Data File:xfd:$
/opt/firefox/plugins/mplayerplug-in.so:$
:$
1138971412000:1:5:$
<a href="http://mplayerplug-in.sourceforge.net/">mplayerplug-in</a> 3.17<br><br>Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using <a href="http://mplayerhq.hu">MPlayer</a> <br>JavaScript Enabled and Using GTK2 Widgets<br>:$
mplayerplug-in 3.17:$
22
0:video/mpeg:MPEG:mpg,mpeg:$
1:audio/mpeg:MPEG:mpg,mpeg:$
2:video/x-mpeg:MPEG:mpg,mpeg:$
3:video/x-mpeg2:MPEG2:mpv2,mp2ve:$
4:audio/mpeg:MPEG:mpg,mpeg:$
5:audio/x-mpeg:MPEG:mpg,mpeg:$
6:audio/mpeg2:MPEG audio:mp2:$
7:audio/x-mpeg2:MPEG audio:mp2:$
8:video/mp4:MPEG 4 Video:mp4:$
9:audio/mpeg3:MPEG audio:mp3:$
10:audio/x-mpeg3:MPEG audio:mp3:$
11:audio/mp3:MPEG audio:mp3:$
12:application/x-ogg:Ogg Vorbis Media:ogg:$
13:audio/ogg:Ogg Vorbis Audio:ogg:$
14:application/ogg:Ogg Vorbis / Ogg Theora:ogg:$
15:video/fli:FLI animation:fli,flc:$
16:video/x-fli:FLI animation:fli,flc:$
17:video/vnd.vivo:VivoActive:viv,vivo:$
18:application/x-nsv-vp3-mp3:Nullsoft Streaming Video:nsv:$
19:video/vnd.divx:DivX Media Format:divx:$
20:audio/basic:Basic Audio File:au,snd:$
21:audio/x-basic:Basic Audio File:au,snd:$
/opt/firefox/plugins/mplayerplug-in-wmp.so:$
:$
1138971412000:1:5:$
<a href="http://mplayerplug-in.sourceforge.net/">mplayerplug-in</a> 3.17<br><br>Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using <a href="http://mplayerhq.hu">MPlayer</a> <br>JavaScript Enabled and Using GTK2 Widgets<br>:$
Windows Media Player Plugin:$
17
0:application/asx:Media Files:*:$
1:video/x-ms-asf-plugin:Media Files:*:$
2:video/x-msvideo:AVI:avi,*:$
3:video/msvideo:AVI:avi,*:$
4:application/x-mplayer2:Media Files:*:$
5:application/x-ms-wmv:Microsoft WMV video:wmv,*:$
6:video/x-ms-asf:Media Files:asf,asx,*:$
7:video/x-ms-wm:Media Files:wm,*:$
8:video/x-ms-wmv:Microsoft WMV video:wmv,*:$
9:audio/x-ms-wmv:Windows Media:wmv,*:$
10:video/x-ms-wmp:Windows Media:wmp,*:$
11:video/x-ms-wvx:Windows Media:wvx,*:$
12:audio/x-ms-wax:Windows Media:wax,*:$
13:audio/x-ms-wma:Windows Media:wma,*:$
14:application/x-drm-v2:Windows Media:asx,*:$
15:audio/wav:Microsoft wave file:wav,*:$
16:audio/x-wav:Microsoft wave file:wav,*:$
/opt/firefox/plugins/mplayerplug-in-rm.so:$
:$
1138971412000:1:5:$
<a href="http://mplayerplug-in.sourceforge.net/">mplayerplug-in</a> 3.17<br><br>Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using <a href="http://mplayerhq.hu">MPlayer</a> <br>JavaScript Enabled and Using GTK2 Widgets<br>:$
RealPlayer 9:$
7
0:audio/x-pn-realaudio:RealAudio:ram,rm:$
1:application/vnd.rn-realmedia:RealMedia:rm:$
2:application/vnd.rn-realaudio:RealAudio:ra,ram:$
3:video/vnd.rn-realvideo:RealVideo:rv:$
4:audio/x-realaudio:RealAudio:ra:$
5:audio/x-pn-realaudio-plugin:RealAudio:rpm:$
6:application/smil:SMIL:smil:$
/opt/firefox/plugins/mplayerplug-in-qt.so:$
:$
1138971412000:1:5:$
<a href="http://mplayerplug-in.sourceforge.net/">mplayerplug-in</a> 3.17<br><br>Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using <a href="http://mplayerhq.hu">MPlayer</a> <br>JavaScript Enabled and Using GTK2 Widgets<br>:$
QuickTime Plug-in 6.0:$
7
0:video/quicktime:Quicktime:mov:$
1:video/x-quicktime:Quicktime:mov:$
2:image/x-quicktime:Quicktime:mov:$
3:video/quicktime:Quicktime:mp4:$
4:video/quicktime:Quicktime - Session Description Protocol:sdp:$
5:application/x-quicktimeplayer:Quicktime:mov:$
6:application/smil:SMIL:smil:$
/opt/firefox/plugins/mplayerplug-in-gmp.so:$
:$
1138971412000:1:5:$
<a href="http://mplayerplug-in.sourceforge.net/">mplayerplug-in</a> 3.17<br><br>Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using <a href="http://mplayerhq.hu">MPlayer</a> <br>JavaScript Enabled and Using GTK2 Widgets<br>:$
Google VLC multimedia plugin 1.0:$
1
0:application/x-google-vlc-plugin:Google Video::$
/opt/firefox/plugins/libvlcplugin.so:$
:$
1138971412000:1:5:$
VLC multimedia plugin <br> <br>version 0.8.4-svn20040920 Janus <br>VideoLAN WWW: <a href="http://www.videolan.org/">http://www.videolan.org/</a>:$
VLC multimedia plugin:$
19
0:audio/mpeg:MPEG audio:mp2,mp3,mpga,mpega:$
1:audio/x-mpeg:MPEG audio:mp2,mp3,mpga,mpega:$
2:video/mpeg:MPEG video:mpg,mpeg,mpe:$
3:video/x-mpeg:MPEG video:mpg,mpeg,mpe:$
4:video/mpeg-system:MPEG video:mpg,mpeg,mpe,vob:$
5:video/x-mpeg-system:MPEG video:mpg,mpeg,mpe,vob:$
6:video/mpeg4:MPEG-4 video:mp4,mpg4:$
7:audio/mpeg4:MPEG-4 audio:mp4,mpg4:$
8:application/mpeg4-iod:MPEG-4 video:mp4,mpg4:$
9:application/mpeg4-muxcodetable:MPEG-4 video:mp4,mpg4:$
10:video/x-msvideo:AVI video:avi:$
11:video/quicktime:QuickTime video:mov,qt:$
12:application/x-ogg:Ogg stream:ogg:$
13:application/x-vlc-plugin:VLC plugin::$
14:video/x-ms-asf-plugin:Windows Media Video:asf,asx:$
15:video/x-ms-asf:Windows Media Video:asf,asx:$
16:application/x-mplayer2:Windows Media::$
17:video/x-ms-wmv:Windows Media:wmv:$
18:application/x-google-vlc-plugin:Google VLC plugin::$
/opt/firefox/plugins/libflashplayer.so:$
:$
1138971412000:1:5:$
Shockwave Flash 7.0 r25:$
Shockwave Flash:$
2
0:application/x-shockwave-flash:Shockwave Flash:swf:$
1:application/futuresplash:FutureSplash Player:spl:$
/home/mike/.mozilla/plugins/nphelix.so:$
:$
1126830606000:1:1:$
Helix DNA Plugin: RealPlayer G2 Plug-In Compatible version 0.4.0.572 built with gcc 3.2.0 on Sep 15 2005:$
Helix DNA Plugin: RealPlayer G2 Plug-In Compatible:$
1
0:audio/x-pn-realaudio-plugin:RealPlayer Plugin Metafile:rpm:$
/opt/firefox/plugins/nphelix.so:$
:$
1138971412000:1:13:$
Helix DNA Plugin: RealPlayer G2 Plug-In Compatible version 0.4.0.572 built with gcc 3.2.0 on Sep 15 2005:$
Helix DNA Plugin: RealPlayer G2 Plug-In Compatible:$
1
0:audio/x-pn-realaudio-plugin:RealPlayer Plugin Metafile:rpm:$

```

It works. I hope it may be of some help.

I have another machine with a PIII CPU on which I'm running the 686 kernel. This has the problems that you report and I'm getting very frustrated trying to work out what's different. Next step, I guess, is to do a line-by-line comparison of this file and its equivalent. Sigh.

---

### Post by jdk_ on 2006-08-06
Hi there,
I have the same problem. Just for the record: I installed the plugin with automatix some time ago, today I reinstalled both acroread and the plugin using synaptic but it is still the same. As has been said before this has been a problem since I started using Dapper (fresh install).

---

### Post by jdk_ on 2006-08-21
I just installed the packages for Acrobat and the plugin that have been posted here:

[http://www.ubuntuforums.org/showthread.php?t=201476&highlight=acrobat+plugin](http://www.ubuntuforums.org/showthread.php?t=201476&highlight=acrobat+plugin)

and now it works :)

---

