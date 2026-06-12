---
title: "flash 7- no sound!"
date: 2006-11-06
forum: General Help
---

### Post by el_ricardo on 2006-11-06
could anyone help me? I think flash is routing audio to the wrong audio device (for some reason there are 2 audio devices on my computer, when there isn't really!) and i can't find settings anywhere to fix this. the same problem has arrisen in flash 9 (through IE6 in wine), however curiosly flash 9 detects both devices in the microphone options! either way this is getting annoying because a lot of flash applets don;t really work (well, they work, but with no sound!)

bottom line- I WANT YOUTUBE TO WORK!

---

### Post by srunni on 2006-11-06
I would suggest using the Flash 9 beta - it has worked flawlessly for me for the past month.
[http://www.adobe.com/go/fp9_update_b1_installer_linuxplugin](http://www.adobe.com/go/fp9_update_b1_installer_linuxplugin)
Just paste the libflashplayer.so file in the download over your current libflashplayer.so file, which is in ~/.mozilla/firefox/plugins , /usr/lib/firefox/plugins , or /opt/firefox/plugins . By the way, if you go to one of these places and the libflashplayer.so is written in italicized font, it's actually a symbolic link to the actual libflashplayer.so, so make sure you find the libflashplayer.so that isn't a link.

---

### Post by el_ricardo on 2006-11-06
ok just tried that, with no luck unfortunately! theres still no sound thanks though, i didn't think flash 9 was available for linux yet (beta or not lol)

---

### Post by el_ricardo on 2006-11-06
got it solved, i had to set the permissions correctly for my plugins folder

---

