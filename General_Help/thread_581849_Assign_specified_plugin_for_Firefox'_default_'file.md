---
title: "Assign specified plugin for Firefox' default 'filetype'-action"
date: 2007-10-19
forum: General Help
---

### Post by perixx on 2007-10-19
Hi... 

I need a way to find and edit the list, where Firefox' looks for specific plugins to open certain file-types with:
 
Preferences > Content > File-type Manager > Change Action > 'specified plugin' (lower-most option)

In the /home/USER/.mozilla/.DEFAULT/mimeTypes.rdf are only the mime-types to be found, that are linked to the file-types - but where can I change the plugins, that are actually connected to those mime-types??

I want to manually fix .mpg default action, so it's opened by the vlc-plugin, not any other (I cannot change this in FF' menu, it's greyed out)!

perixx

---

### Post by TearDownAllSigns on 2007-10-19
I think they got your answer here, I'm about to try it myself. Totem has been driving me batty.

[http://ubuntuforums.org/showthread.php?t=575829&highlight=vlc+firefox+plugin]("http://ubuntuforums.org/showthread.php?t=575829&highlight=vlc+firefox+plugin")

---

### Post by TearDownAllSigns on 2007-10-19
So basically the only way I've found to change the default plug-in is to delete totem:
```
sudo rm /usr/lib/firefox/plugins/libtotem* 
```
And if you have another one already installed it should appear in the grayed out area for "Use this Plugin" under each file type.

I tried out VLC,
```
sudo apt-get install mozilla-plugin-vlc
```
 and it worked for a few sites but I couldn't control the movies other than to full screen them. I think you have to do some custom java script to get the controls. 

Ended up with mplayer and it seems to work and look great. 
```
sudo apt-get install mplayer mozilla-mplayer -y
```

---

### Post by perixx on 2007-10-21
Well, 

Totem has awful colours and isn't very interactive, but surely a lot more than VLC. The latter is one of the best video-qualitiy players for my taste, plus it's very compatible to most formats. Alas, VLC tends to step up with 'Visualization', overwriting the video output, unless I leave full-window-playback - and you got no control over the videos at all - and I cannot play .wmv files with it!

The only 2 plugins that seamlessly insert the videos into the FF-window, are Totem and VLC, so it seems. Totem can play nearly everything (including WMV) with gstreamer, that's a BIG plus! But I cannot do anything about video ratio and bad colours - that's really annoying at the same time!

Gxine REALLY sucks, can only play back a handful of formats and won't integrate into the FF windows - also, it lacks of features.

Mplayer lacks of features, won't integrate into FF-window and can't play some files, most especially .wmv - so also not an option....

I have set up the following so far: Totem/gstreamer for FF-integrated clips for fast (pre-)viewing. And VLC as my main-videoplayer with good quality - for downloaded files or media; it works allright. 

For audio files - I'm still experimenting, but for media, 'CD player' seems fast and reliable and XMMS or Ryhtmbox might suit my needs for better format-support. Don't know how they integrate into FF by now, though -- there, Mplayer might have an advantage, if I'm not mistaken.


The problem is: if I install multiple apps for handling multimedia streams in FF, the 'default plugin' option will most certainly be captured by one plugin, keeping me from using another plugin for different media (like music) - that's what I actually would like to solve!


perixx

---

### Post by rand0m on 2007-11-15
For me the mplayer plugin is the best. Has more features than vlc/totem but I want to use totem for one specific media type as well. Any luck with this issue?

---

### Post by perixx on 2007-11-21
Well rand0m,


I had a dual-player/streamer setup already. But I cleaned out the gstreamer-trash (horrible video quality... unless I made some mistake). I suppose you'll have to install the respective apps and streamer- + browser-plugins: 
mplayer, vlc, totem-mozilla, mplayer-plugin, gstreamer (good, bad & ugly sets), w32codecs...

Then you should be able to assign a certain app / streaming plugin within FF-menu (preferences > content > Manage... file types. Of course, I don't know, which specific media-type you're referring to. And, as I said, totem-plugin will most probably snatch away the filetype-handling of some mime-types (.wmv ?)... at least, that's what I've experienced; I've been looking for a solution to set up FF' mime-type-configuration manually, but couldn't find one so far. Btw., don't forget to set your video-driver in mplayer (and vlc ?) to 'xv' (should be the most compatible one), if you encounter error messages on playing vids.


perixx

---

### Post by rand0m on 2007-11-21
My problem was that I wasn't able to select/assign a different plugin in the firefox preferences. Manually assigning them didn't seem to do anything and I couldn't change anything for the "Use This Plugin" option. Right now I'm using [this]("https://addons.mozilla.org/en-US/firefox/addon/446") firefox extension and it does what I'm looking for.

---

### Post by perixx on 2007-11-21
ah, ok... the connectivity-plugin... I've read about this little helper several times but refused to install it, due to some negative responses about things getting messed up with that.
I tried to find out, WHERE those plugin's are specified for FF, but none could give an answer to this.

perixx

---

### Post by rand0m on 2007-11-23
Yeah, I've had no problems yet. I only assign windows media types in the extension (they refuse to play with the embedded mplayer plugin although external smplayer is fine). Everything else is left default. If you ever find out please post it here :).

---

### Post by perixx on 2008-01-09
*giving it another try*

---

### Post by philinux on 2008-01-09
If you want to see the full list.

Goto 

```
about:config
```

filter

browser.download.hide_plugins_without_extensions  Change it to false

---

### Post by perixx on 2008-01-09
Hello Philinux :) 

You said to search in about:config; filtering it for mime gives this in return:
> helpers.private_mime_types_file --> ~/.mime.types
> helpers.global_mime_types_file -->/etc/mime.types
The first file is not there, the second one only shows mime-definitions; what I want to find out is, in which file those definitions (e.g. 'wmv') are linked to certain applications (such as plugins or external apps)...

perixx

---

