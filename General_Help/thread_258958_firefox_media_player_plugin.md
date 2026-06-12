---
title: "firefox media player plugin"
date: 2006-09-16
forum: General Help
---

### Post by feest on 2006-09-16
hi, when i want to watch movies on the web firefox needs the windows mediaplayer plugin, since thats for windows, that's not gonna work (the easy   way) i have crossover and i have installed windows media player but it doesn't work for firefox, i also have installed ms ie but that's highly unstable so is there any other plugin wich allows you to play windows media files (wmv) and other files for windows media player) or can i install the plugin for linux? please help

sven

---

### Post by Cynical on 2006-09-16
Looks like you went through a lot of trouble.

First install [w32codecs](http://packages.freecontrib.org/plf/pool/dapper/non-free/w32codecs_20060611-1plf1_i386.deb), this will allow you to play wmv, quicktime, and realplayer formats.

Then do
```

sudo apt-get install totem-xine totem-xine-firefox-plugin

```
to play the media using totem. 

(you can use other players like mplayer/kaffeine, but personally I like how totem's controls look)

---

### Post by feest on 2006-09-18
no that doesn't work for me i need it to run in the firefox browser ike the media player plugin for windows, i can play wmv files using media player (wine) but i need the media player in the broswer...

---

### Post by UKer on 2006-09-18
Either the totem or mplayer plugin for firefox allows you to play most wmv files in firefox, I use the latter and this works with almost all Media Player and Quicktime files I've tried. Make sure you have w32codecs installed, as Cynical mentioned.

---

### Post by feest on 2006-09-18
cool it works, but the progress bar isn't ticking...

---

