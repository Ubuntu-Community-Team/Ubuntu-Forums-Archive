---
title: "Totem, w32codec and files association"
date: 2005-05-20
forum: General Help
---

### Post by LinxNew on 2005-05-20
Hi,

I've read ubuntuguide, and I've installed w32codec from synaptic.
Installation was succesful, but when I try to play some divx I have the same error:
no codec found   :-? 

Other question:
How can I tell to XMMS or Beep to be my default player for music files ?

When I open an mp3, Totem open itself and doesn't play :-| 

Thank you

---

### Post by Knome_fan on 2005-05-20
1. Make sure to use totem-xine not totem-gstreamer if you want the w32codecs to work.

2. Open nautilus, right click on an mp3 file, choose preferences, choose open with and select the app you want it to be associated with.

3. You probably need to install gstreamer0.8-mad from universe to get gstreamer mp3 support. (For totem-gstreamer and rhythmbox for example)

---

### Post by LinxNew on 2005-05-21
> 1. Make sure to use totem-xine not totem-gstreamer if you want the w32codecs to work. 

 :-? 

I use Totem Movie Player. The only that I can see in Audio&Video menu.

---

### Post by NeoChaosX on 2005-05-21
It may say "Totem Media Player" on the menu, but the xine version of the program is more compaible with other codecs than the gstreamer-based one that's installed by default. Just enter "sudo apt-get install totem-xine" in the Terminal, and that'll get it working.

---

### Post by LinxNew on 2005-05-25
> 2. Open nautilus, right click on an mp3 file, choose preferences, choose open with and select the app you want it to be associated with. 

I browse in my hd and when I find mp3 file I right click and choose preference.
But I cannot choose to associated with a program. Now I must use right click to select xmms, but with left click, totem open itself. :-?

---

### Post by lorap on 2005-05-25
hi friend!
install this codec - gstreamer0.8-ffmpeg
have a nice day.
pavel

---

