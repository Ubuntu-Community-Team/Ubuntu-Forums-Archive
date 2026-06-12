---
title: "Mplayer plugin for firefox=no sound"
date: 2005-03-26
forum: General Help
---

### Post by Nego on 2005-03-26
Well, I installed mplayer and the mozilla-mplayer plugin from the ubuntu respositories. I can view all videos with firefox just fine, but I don't get any sound; NONE of the videos I play give me any kind of sound. I've seen many different issues like this, but none have given me any success. When I use mplayer outside of firefox I get sound btw.

---

### Post by ACK!! on 2005-03-26
[QUOTE=Nego]Well, I installed mplayer and the mozilla-mplayer plugin from the ubuntu respositories. I can view all videos with firefox just fine, but I don't get any sound; NONE of the videos I play give me any kind of sound. I've seen many different issues like this, but none have given me any success. When I use mplayer outside of firefox I get sound btw.[/QUOTE]

Did you get the w32codecs?

I needed those before I got sound with sorrenson quicktime videos like you see on Apple Quicktime sites.  

Its a big *ss package btw but worth it for smooth video.  

Good luck and if that was not it then sorry.

---

### Post by arnieboy on 2005-03-26
use the following commands at terminal:
$ wget [http://ftp5.mplayerhq.hu/mplayer/releases/codecs/essential-20040922.tar.bz2](http://ftp5.mplayerhq.hu/mplayer/releases/codecs/essential-20040922.tar.bz2)
$ sudo mkdir /usr/lib/win32/
$ tar -xjf essential-20040922.tar.bz2
$ sudo cp essential-20040922/* /usr/lib/win32/

all sound will run after that. check by going to [www.apple.com/trailers](www.apple.com/trailers) for example and playing one of the movie previews

---

### Post by Nego on 2005-03-26
Tried it, no dice...  #-o

Does it matter that I have the newer codecs?

---

### Post by c_dog on 2005-03-26
This one was gettting to me a little earlier this evening. There seems to be some conflict with esd and alsa/oss sound mixers. Try going into your System-Prerences-Sound menu and uncheck the 'enable sound server at startup' box on the General tab. Log out and restart. Videolan vlc was Mplayer's sound started working after this, but the start-up and shut-down chime will go away.

---

### Post by Nego on 2005-03-26
No luck, my mplayer sound works fine, but the sound in firefox does not work with ANY of the movies I try to play.

//Fixed, it figures the only post i didnt read would fix the problem, I decided just to dl ALL of the codecs and put them in /usr/lib/win32 and it fixed it. Thanks guys!  =D>

---

### Post by pefdus on 2005-07-09
The link to the essentials codec package has changed (old one was obsoleted).

Try 

wget http://ftp5.mplayerhq.hu/mplayer/releases/codecs/essential-20050412.tar.bz2
sudo mkdir /usr/lib/win32/
tar -xjf essential-20050412.tar.bz2
sudo cp essential-20050412/* /usr/lib/win32/

---

### Post by slothjammin on 2005-07-15
This guide fixed it for me
[http://www.sysop.ca/?p=26](http://www.sysop.ca/?p=26)
Here is what it states, *"I did a quick google and found that mplayer plugin has it’s own config file for mplayer’s options under /etc/mplayerplug-in.conf . In Ubuntu all of the options in the file are commented out by default so you have to go in and configure what sound output engine you prefer (esd if you’re using the default Gnome install). This is what was crashing mplayer for me, once I set esd as the default output all my media played fine."*

-Slothjammin

---

