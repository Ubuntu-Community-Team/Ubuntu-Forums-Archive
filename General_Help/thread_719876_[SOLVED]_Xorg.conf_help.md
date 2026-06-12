---
title: "[SOLVED] Xorg.conf help"
date: 2008-03-09
forum: General Help
---

### Post by spaceboy909 on 2008-03-09
[B]

SOLVED![/B]

(Gutsy w/ Nvidia and widescreen LCD)

I just modified my xorg.conf via 'dpkg-reconfigure xserver-xorg', and now I'm getting the "greeter application is crashing" error.

I have a Samsung 225BW widescreen monitor, and I was trying to add in the native resolution into Xorg.conf.  I opted for the advanced settings so I could manually input the frequencies (which I got from the manual) as I wasn't sure if the simpler route would detect them properly (will it?  Or is advanced best if it won't autodetect the monitor?).

It was after this that I got the error.

Does this indicate that my editing of xorg.conf was faulty, or is there something else going on?  I did make a backup of the file, but I really want to get the native resolution up and running.

Any help is appreciated.

....as a sidenote, when I was in the Gnome 'screen/res' panel the other day, I noticed that it did have my exact monitor model listed, but when I selected it, it asked for a driver file, and there is no Linux driver for this model yet.  I thought that was a bit strange that it had the model list for models it doesn't support....?

---

### Post by spaceboy909 on 2008-03-09
It took some tinkering but I got the new specs input by hand.  At first, inputing the new specs was still generating the error, but that was with editing the newly auto-generated xorg.conf file.  So I retrieved the backup file, edited it, and now I've got 1680x1050.  I left the color depth set at 24, even though Samsung says it is '8' for this monitor.....I don't understand that; why a modern monitor would be limited to 8; I have a feeling that may be a typo on their part.

---

