---
title: "Crash(es)"
date: 2015-07-08
forum: General Help
---

### Post by Leo_Gould on 2015-07-08
Please help me Ubuntu forums, you are my only hope.

I'm a seasoned user of ubiquitous nut and Linux in general (over a decade now I think about it!)

but recently my 14.04 installation on my laptop has been very buggy. I purchased a new 128GB microsd card recently to store my music on and I'm just copying my music over to it, I only have put 30.1GB of music on it and it crashes my system every time without fail. Attached is the error printed error: [IMG]https://www.dropbox.com/s/oyy5wxqckiyf83j/dsc_0048.jpg?dl=0[/IMG]

i don't think it's a problem with nautilus as I have tried Thunar and it kicks out the same error. Is it the card or my lappy do you think?

As well as this my laptop has become very sluggish and constantly disconnects from my wireless network.

Any input would be appreciated!

cheers,

-Leo

---

### Post by tgalati4 on 2015-07-09
Boot the laptop and open a terminal.

```
dmesg | more
```

Spacebar to page forward, "q" to quit.  Look for errors related to the SD card reader.  Perhaps your SD-to-Micro adapter is faulty.  Try a different one.

It's possible that your adapter does not handle 128 GB size cards.  Check the specifications of your reader.

---

### Post by Leo_Gould on 2015-07-12
> **tgalati4 said:**
> Boot the laptop and open a terminal.

```
dmesg | more
```

Spacebar to page forward, "q" to quit.  Look for errors related to the SD card reader.  Perhaps your SD-to-Micro adapter is faulty.  Try a different one.

It's possible that your adapter does not handle 128 GB size cards.  Check the specifications of your reader.

Thanks for the suggestion. I couldn't really see anything relating to the SD card, but I don't think it's the adapter.-When I plug it into my mp3 player and try it that way, it just kicks out the same error.

Cheers

-Leo

---

