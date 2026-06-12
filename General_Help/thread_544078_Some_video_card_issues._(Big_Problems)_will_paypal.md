---
title: "Some video card issues. (Big Problems) will paypal if solved."
date: 2007-09-05
forum: General Help
---

### Post by Crafty Kisses on 2007-09-05
So a little over 6 months now I've had this huge issue, so heres the deal. Well I have a NVIDIA GeForce 6800 GT, and I was wondering what drivers I should install, because I tried to just enable the drivers from the restricted drivers manager, but when I did that it said something to the extent of "Ubuntu cannot support the new Hardware" or something to that nature, the screen was all distorted and stuff, and it was all messed up, but I uninstalled the drivers and it everything has been working properly, but I can't view sites with a lot of flash or my computer freezes. :(, Here's some of the screenshots of what happens when I install my drivers for my Video Card:

[IMG]http://i81.photobucket.com/albums/j216/codenamexiii/Screenshot-8.png[/IMG]

[IMG]http://i81.photobucket.com/albums/j216/codenamexiii/Screenshot-1-4.png[/IMG]

[IMG]http://i81.photobucket.com/albums/j216/codenamexiii/Screenshot-9.png[/IMG]

Specs:
AMD Athlon 1800+
1 GB of Ram
40 GB HDD
GeForce 6800 GT

---

### Post by Crafty Kisses on 2007-09-05
For the record, I've already tried Envy, and that had the same outcome. :(

---

### Post by Dark Hornet on 2007-09-06
--well crap...there went my solution...lol.  I have the same gfx card in my box, and I used Envy, and downloaded the latest drivers for nVidia, and everything works great.

I do have a question....I would be curious to see if installing Ubuntu 7.04 from scratch, then doing all of the updates, THEN installing the nVidia drivers would work...just a thought...anyway, good luck.

---

### Post by Crafty Kisses on 2007-09-06
> **Dark Hornet said:**
> --well crap...there went my solution...lol.  I have the same gfx card in my box, and I used Envy, and downloaded the latest drivers for nVidia, and everything works great.

I do have a question....I would be curious to see if installing Ubuntu 7.04 from scratch, then doing all of the updates, THEN installing the nVidia drivers would work...just a thought...anyway, good luck.

That's actually what I did, and still the same outcome. :( Ah, well.

---

### Post by ~LoKe on 2007-09-06
Boot up a LiveCD and see if it still happens.  If it does; bad video memory (card is TOAST).

---

### Post by artinla on 2007-09-06
That doesn't look like a video memory problem.  It is more likely that the NVidia driver is more aggressive clocking the card or video port.  There are utilities available to underclock/overclock NVidia cards in Linux, I suggest that you install one and adjust your clock speeds to a lower setting.
Also, it is possible that you might have to set your AGP port (I assume that the 6800 is AGP) to a lower transfer rate I/E 4x or even 2x.

The 6800GT was basically an overclocked 6600 with hand picked "Top Shelf" RAM.  They were only produced at first so that NVidia had something that would compete with  the ATI 9800.  If the RAM gets even slightly weak, the cards do what yours is doing.  It is very common with the 6800GT because the cards were running on the "Ragged Edge" and being pushed to the clocking limits to be competitive.  NVidia only produced limited numbers of the 6800GT so that they could boast of having the fastest card over ATI, but their real goal was to sell lots and lots of 6600's which had a far greater profit margin and were nearly as fast as the 6800's.  

I think you will be able to get it to work properly with a little clock tweaking.

Good Luck

PS..  If your video is screwed up when using the LiveCD, your card is toast just as the above poster suggested.

---

### Post by sloggerkhan on 2007-09-06
I think the screw up is only happening with binary drivers, not with open source, which means live CD would be working fine....

---

### Post by Crafty Kisses on 2007-09-06
> **artinla said:**
> That doesn't look like a video memory problem.  It is more likely that the NVidia driver is more aggressive clocking the card or video port.  There are utilities available to underclock/overclock NVidia cards in Linux, I suggest that you install one and adjust your clock speeds to a lower setting.
Also, it is possible that you might have to set your AGP port (I assume that the 6800 is AGP) to a lower transfer rate I/E 4x or even 2x.

The 6800GT was basically an overclocked 6600 with hand picked "Top Shelf" RAM.  They were only produced at first so that NVidia had something that would compete with  the ATI 9800.  If the RAM gets even slightly weak, the cards do what yours is doing.  It is very common with the 6800GT because the cards were running on the "Ragged Edge" and being pushed to the clocking limits to be competitive.  NVidia only produced limited numbers of the 6800GT so that they could boast of having the fastest card over ATI, but their real goal was to sell lots and lots of 6600's which had a far greater profit margin and were nearly as fast as the 6800's.  

I think you will be able to get it to work properly with a little clock tweaking.

Good Luck

PS..  If your video is screwed up when using the LiveCD, your card is toast just as the above poster suggested.
So do you think I should switch to a different card, I have a GeForce Ti4200, that might work better, do you think it will?

---

### Post by artinla on 2007-09-06
Yeah, the 4200 will probably work fine.  If you plan to game, then you may want to focus on tweaking the 6800.  If not, go with the 4200.

I have a 6800GT and it did the same thing yours is doing.  I ended up getting it to work by underclocking it.  When I switched over to PCI Express and a 7900GS, the problem went away.

---

### Post by Crafty Kisses on 2007-09-06
> **artinla said:**
> Yeah, the 4200 will probably work fine.  If you plan to game, then you may want to focus on tweaking the 6800.  If not, go with the 4200.

I have a 6800GT and it did the same thing yours is doing.  I ended up getting it to work by underclocking it.  When I switched over to PCI Express and a 7900GS, the problem went away.

Do you know what the program is called?

---

### Post by artinla on 2007-09-07
The one that I use is called nvclock.  You can read about it at [http://www.linuxhardware.org/nvclock/](http://www.linuxhardware.org/nvclock/)

It is in the universe repository

sudo apt-get install nvclock

---

