---
title: "[SOLVED] cant put music onto my mp3 player"
date: 2008-06-17
forum: General Help
---

### Post by ayeshap on 2008-06-17
yesterday i bought a samsung yp-k3jqb 2gb mp3 player. i was able to put songs from my desktop (which has windows) onto the player. however, my laptop,which contains ubuntu is what i mainly use. i plugged in the player but the only thing that comes up is a music player and when i drag my music into the player, its not saving on the mp3. neither can i see the songs which i placed on my mp3 yesterday from windows pc.
the cd that comes with the mp3 player is not installing either.

---

### Post by change_mode on 2008-06-17
I suppose you mean the audio player that automatically pops up when you connect the mp3 player?

There should also be an icon on your desktop when you connect the mp3 player. Double click the icon and it will open Nautilus, the file manager. Copy / Paste your items in there, not into the music player.

When you are done right-click on the desktop item, select "Unmount" and disconnect the device.

Good luck :)

---

### Post by Tom--d on 2008-06-17
The CD will be for Windows and maybe Mac. 

Linux, however, should work out of the box for it.

And yes, In Ubuntu, the default format for music is ogg (musicname.ogg)
You can change this in your music player.

If you want mp3 encoding support (makes .mp3 files for your mp3 player) do this in terminal:
```
sudo apt-get install gstreamer0.10-plugins-ugly-multiverse
```

To convert the music to mp3, you need to use a sound converter.
```
sudo apt-get install soundconverter
```

Then, Apps > Sound > Sound Converter > Options > MP3 (tick it, its at the bottom)

Then add your music you want to convert. Then drag over those files onto your mp3.

Also, converting a loss format to a loss format will offer a reduction in qulitay :(

Hope this helped,
Tom

---

### Post by ayeshap on 2008-06-17
there isnt an icon on the desktop when i connect the mp3 player.the first time i connected it there was one but since then it hasnt come up again.

---

### Post by change_mode on 2008-06-17
Did you unmount the player before removing it? If not, restart your system and then connect it again.

---

### Post by Tom--d on 2008-06-17
Plug the mp3 player in before you turn on your pc.

See if it comes up.

---

### Post by ayeshap on 2008-06-17
i have tried both change_mode and Tom--d's suggestions and an icon still isnt coming up, only the player. 
could it be because i put in the cd rom?

---

