---
title: "problems with MPlayer"
date: 2005-04-26
forum: General Help
---

### Post by pvphaneuf on 2005-04-26
I have currently installed MPlayer along with the multimedia codecs and the DVD playback capabilities that were all cited on the Unofficial Ubuntu 5.04 Starter Guide ([http://ubuntuguide.org/)](http://ubuntuguide.org/)). The probleme is when I try to stream a movie off the internet I get the Mozilla plug-in window telling me its buffering but after downloading the window always freezes and MPlayer never play the media. It has happened to me everytime. Could someone offer me some advice on how to fix this problem. 

Thanks in advance

---

### Post by cdhotfire on 2005-04-26
```

$ sudo dpkg-reconfigure mplayer-386
$ sudo dpkg-reconfigure mozilla-mplayer

```

?

---

### Post by pvphaneuf on 2005-04-26
no dice, I'm still getting the freeze up on my plug-in/buffering window.

---

### Post by cdhotfire on 2005-04-26
have you tried removing them, and then installing them again?

---

### Post by DutchLau on 2005-04-26
I had the same problems before. You're probably installing Mplayer when you have Firefox open or something. Uninstall the packages via apt-get or Synaptic Package Manager, and reinstall them without your browser open. Give the computer a restart and Mplayer *should* be up and going  :) 

Good luck!

---

### Post by pvphaneuf on 2005-04-26
YEAH, works great. Y'all are on my shoutout list for when I get famous!

---

### Post by cdhotfire on 2005-04-26
[QUOTE=pvphaneuf]YEAH, works great. Y'all are on my shoutout list for when I get famous![/QUOTE]

lol, anytime sir.:)

---

### Post by DutchLau on 2005-04-26
I think he was talking to me cdhotfire  ;-)  

Just contributing (even though I'm a Linux newbie  :) )

---

### Post by cdhotfire on 2005-04-26
[QUOTE=DutchLau]I think he was talking to me cdhotfire  ;-)  

Just contributing (even though I'm a Linux newbie  :) )[/QUOTE]

Perhaps, im blind, but he said y'all (meaning more than one). Onless you are superhuman and you count for more than one person, if so sorry.:)

---

### Post by DutchLau on 2005-04-26
Point taken  :)  But perhaps you *are* blind  :razz: 

Btw, are there any other interesting Linux movie players besides VLC, Mplayer and Totem (which totally sucks)?

---

### Post by cdhotfire on 2005-04-30
i 100% agree that totem sux. Theres xine, which is quite good. Also you can try kaffeine whish is a kde movie player, and is also a good player.  You can try those, they are the only good ones ive heard about. Xine i like because it lets you set square ratio to movie, just incase its a widescreen, wish makes the movie spread move throughtout the screen, and this is not able to be done in vlc, at least to my knowledge.

---

### Post by DutchLau on 2005-04-30
True, I'm already using Gxine which is pretty neat. Nice interface, simple, clean! The way it's supposed to be! Mplayer is too flashy.

---

