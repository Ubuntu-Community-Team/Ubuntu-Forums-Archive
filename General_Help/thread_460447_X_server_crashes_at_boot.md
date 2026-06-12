---
title: "X server crashes at boot"
date: 2007-05-31
forum: General Help
---

### Post by Stepes on 2007-05-31
Hi all. Maybe this is the wrong section so sorry. I use Kubuntu 6.10. I recently installed this game: [http://www.ufoot.org/liquidwar/v5](http://www.ufoot.org/liquidwar/v5) which is pretty funny. But every time I played it when I quit the game, the desktop was zoomed in. When I moved my mouse to the sides the desktop panned that way! I had to go and change the resolution to something else and back to the one I wanted for everything to be ok. 
But the third time I played I couldn't get the resolution back so I restarted.

And since then I can't get to the kde login screen. After the loading splash I get a console login. Then I try to start the X server with startx or xinit and nothing works. I get this error:

Fatal server error:
no screens found
XIO: fatal IO error 104 (connection reset by peer) on X server ":0.0" after 0 requests (0known processed) with 0 events remaining.
xauth: error in locking authority file /home/stefanos/.Xauthority

with kdeinit I get:
Aborting. $DISPLAY is not set.

I tried the commands with sudo, same thing.

Also when the loading splash starts I also get a few errors of this type which I think are harmless cause I got the from the start: [17179570.024000] PCI: Cannot allocate region 7 of bridge 0000:00:1c.0

I have an acer aspire 3680 with intel 940 gml grafics card. I use 915resolution for my resolution.
Also some time ago I went messing around trying to install a screensaver, namely KCometen
[http://www.kde-look.org/content/show.php/KCometen3+for+Sflack?content=56744](http://www.kde-look.org/content/show.php/KCometen3+for+Sflack?content=56744)

But trying to get it to install running make and make install or whatever it needed, I somehow got my desktop to crach whenever I tried to change background settings. Afterwards I reinstalled 915resolution and this problem was fixed. But since then no screensaver works on my laptop. I only get a big white X as a screensaver.

Any help on this issue would be great, thanks
(I believe those two problems are kinda linked, maybe :P)

---

### Post by Stepes on 2007-05-31
hm I copied xorg.conf.1 over xorg.conf and now it booted up perfectly....Although I am kinda afraid it might happen again.
What are those xorg.conf.1-4 files?

---

