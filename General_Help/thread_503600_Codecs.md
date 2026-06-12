---
title: "Codecs"
date: 2007-07-18
forum: General Help
---

### Post by durkhrod chogori on 2007-07-18
I am trying to play all my music and video files from Windows. I clicked on one of each and in both cases and Ubuntu's media player (not sure what it is though) is asking me to install the required codecs to play/view them. It is prompting me to download them (the search is done by the OS itself). However, it also warned me that they are not supported and errors may occur.

Now most of you here have experienced the same thing in the past and have dealt with it efficiently.

So what do I do? Maybe I should install another Media Player as the default one is not the best.

I appreciate your help.


Cheers.

---

### Post by mikewhatever on 2007-07-18
Well, the default player, Totem, is ok. Obviously, Ubuntu does not support Windows codecs, hence the message you get. You might want to check vlc player too.

---

### Post by durkhrod chogori on 2007-07-18
OK, I see. But what do I need to do to play my Windows files in Ubuntu.

Thnx.

---

### Post by EndPerform on 2007-07-18
The codecs are pretty stable as I've been using them for as long as I've had an install, which is a while now.  You shouldn't have too much trouble with them.

---

### Post by Hallvor on 2007-07-18
If you use Feisty: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Codecs](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Codecs)

> sudo apt-get install ubuntu-restricted-extras libxine-extracodecs gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-pitfdll


> sudo apt-get install w32codecs


You could also just install XMMS for mp3 (Winamp clone) and VLC media Player for video, since they use their own codecs and do not need other codecs than their own. (VLC can play mp3 too.)

Copy and paste to a terminal:

> sudo apt-get install xmms xmms-skins xmms-wma

and

> sudo apt-get install vlc vlc-plugin-*

---

### Post by mikewhatever on 2007-07-19
A good source of information would be [www.help.ubuntu.com](www.help.ubuntu.com). Search for 'restricted formats'.

---

