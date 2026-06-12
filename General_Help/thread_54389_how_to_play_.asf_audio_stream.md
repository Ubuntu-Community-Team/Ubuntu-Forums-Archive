---
title: "how to play .asf audio stream?"
date: 2005-08-04
forum: General Help
---

### Post by glandula on 2005-08-04
just wondering how to play a radio stream in the asf format. it wont play in bmp, in vlc is very jerky, in totem it sometimes works, but often not

also, whats with the bookmark/playlist in vlc and totem ? u cant save anything, its all gone if you restart the programs

---

### Post by varunus on 2005-08-04
Did you install codecs as per the ubuntu guide?  [http://www.ubuntuguide.org](http://www.ubuntuguide.org)

Is the stream jumpy on windows, or just Ubuntu?

---

### Post by glandula on 2005-08-04
yeah all codecs installed and then some. no not jumpy in windows. windows had some nice online radio apps such as [http://www.screamer-radio.com/](http://www.screamer-radio.com/) that could play virtually anything. must admit i havent really thought about looking for something like screamer radio for ubuntu yet. probably a good idea to try. know any? yeah i know rythmbox but it cant play the asf it seems

---

### Post by Xterminator on 2005-08-04
[QUOTE=glandula]yeah all codecs installed and then some. no not jumpy in windows. windows had some nice online radio apps such as [http://www.screamer-radio.com/](http://www.screamer-radio.com/) that could play virtually anything. must admit i havent really thought about looking for something like screamer radio for ubuntu yet. probably a good idea to try. know any? yeah i know rythmbox but it cant play the asf it seems[/QUOTE]

```
sudo apt-get install streamtuner streamripper
```

optionally install **gxine** to play the ASF radios.

[http://www.nongnu.org/streamtuner/](http://www.nongnu.org/streamtuner/)
[http://streamripper.sourceforge.net/](http://streamripper.sourceforge.net/)

---

### Post by glandula on 2005-08-04
gxine looks like what i wanted :D thanks guys

---

### Post by Xterminator on 2005-08-04
[QUOTE=glandula]gxine looks like what i wanted :D thanks guys[/QUOTE]

i'm use only streamtuner and gxine to streaming radios
streamtuner supor xiph,live365,shoutcast,and local files
if streamripper installed you record the streams :-)

Sorry my english ;-)
see gxine in action the powerfull configurable xine in GTK2 
ASF radio
[http://xterminator.multiply.com/photos/photo/13/47.png](http://xterminator.multiply.com/photos/photo/13/47.png)
[http://xterminator.multiply.com/photos/photo/13/49.png](http://xterminator.multiply.com/photos/photo/13/49.png)
[http://xterminator.multiply.com/photos/photo/13/51.png](http://xterminator.multiply.com/photos/photo/13/51.png)
Quicktime vídeo
[http://xterminator.multiply.com/photos/photo/1/100.png](http://xterminator.multiply.com/photos/photo/1/100.png)
WMV Vídeo
[http://xterminator.multiply.com/photos/photo/1/104.png](http://xterminator.multiply.com/photos/photo/1/104.png)
Configuration tool urghhhh totem has no options :P
[http://xterminator.multiply.com/photos/photo/1/102.png](http://xterminator.multiply.com/photos/photo/1/102.png)

---

### Post by glandula on 2005-08-04
where do u find gxine skins? or isnt that a skin? i looked for them but couldnt find anything. also gxine seems to misbehave a bit when changing frmo one stream to another. it simply freezes. but hey i like it anyway

---

### Post by Xterminator on 2005-08-04
[QUOTE=glandula]where do u find gxine skins? or isnt that a skin? i looked for them but couldnt find anything. also gxine seems to misbehave a bit when changing frmo one stream to another. it simply freezes. but hey i like it anyway[/QUOTE]

gxine uses gtk-theme , not skins in the ASF sceenshot is my theme Xterm-Nice
but is broke , it was a light theme, but they had changes in smooth-engine and it does not work more..

you can configure many things in it, habilie the configuration option to **master of known universe**

**File->Preferences->experience level**

---

