---
title: "[SOLVED] Curious AWN / Desktop Behavior at Startup"
date: 2008-06-26
forum: General Help
---

### Post by EricCFlem on 2008-06-26
Hey -

Just a little befuddlement on my part here.  I'm running 8.04, with all the updates installed, on a Dell Dimension 3000 with a Geforce FX 5200 video card.  I'm running Gnome, have Compiz Fusion on to Normal Effects (although I've also tweaked a few Compiz settings in the Advanced Desktop Effects Settings), and have Avant Window Navigator set to start up whenever I boot up the computer.

Everything is running fine, but each time I boot up, it's as if the computer freezes... but just for a couple seconds.  I get most of the desktop, but where Avant Window Navigator should be appearing, all I see is this rectangular white box.  Actually, if you watch how AWN loads up the first time, with the bar rising up from the bottom of the screen and all the icons scrolling in from the right... it's as if that animation (for whatever reason), is unable to be shown, so the Desktop just defaults to showing the white block... at least until AWN is ready to be showed.

There's also a smaller white box (that I have no explanation for), in the upper left corner of the screen.

This isn't a huge deal, but I would like it fixed RIGHT NOW.  :-D

Anyway, I'm hoping someone out there has some idea why this is happening.

Oh!  I'm also running the nvidia-glx-new drivers that are in the repository... version 169.12, or something.

If anyone has any idea why this is happening, and a possible fix (assuming it can be fixed), that would be awesome.

Thanks!

Eric

P.S.  I'm attaching a made-up screen shot that approximates what I'm talking about (I couldn't actually get a screen shot while the weirdness was happening, so this is as close as I can get).  Thanks!

---

### Post by phynix on 2008-06-26
Ya I get the same thing as well.

---

### Post by pmaconi on 2008-06-26
his happens because AWN starts before Compiz. A solution is to have an autostart script open Awn after 10 seconds or so instead of immediately. You would also need to figure out the other program that is starting and put that in the script as well. 

Here is an example of such a script. ```
!# /bin/bash

sleep 10;
avant-window-navigator &
```

You would need to add that to an executable file and add the file to your sessions list.

---

### Post by sjs889 on 2008-06-26
Sadly the above advice doesn't seem to improve the situation:(

---

### Post by pmaconi on 2008-06-26
I made a typo. Try: ```
#! /bin/bash

sleep 10;
avant-window-navigator &
```

---

### Post by Doji on 2008-06-26
Those of us with slower computers may have to increase the sleep time as well. Mine's 15.

---

### Post by EricCFlem on 2008-06-26
> **pmaconi said:**
> I made a typo. Try: ```
#! /bin/bash

sleep 10;
avant-window-navigator &
```


Thanks!  That worked for me.  Oddly enough, though, once I did that, both white blocks disappeared, the one on the top and the bottom.  Problem solved.  :-)

At least for me.

Thanks again!

---

### Post by badfish591 on 2008-06-26
sweet, i always wondered why awn did that. the script worked perfectly.

---

### Post by magicmanfk on 2008-06-27
> **EricCFlem said:**
> Thanks!  That worked for me.  Oddly enough, though, once I did that, both white blocks disappeared, the one on the top and the bottom.  Problem solved.  :-)

At least for me.

Thanks again!

ok, so if someone can tell me what I'm doing wrong, I'd appreciate it. :)

I copied the code from the post (the second post), then opened text editor, pasted it, saved it in home, then went to "Sessions", took away AWN, and added that instead. When I tried to restart the computer, awn didn't come up at all. Anyone know where I messed up?

~Franklin

---

### Post by pmaconi on 2008-06-27
Right click the file you added and make sure you check the box that says allow executable.

---

### Post by magicmanfk on 2008-06-27
thanks, that's exactly what I needed to do! And such a quick reply too!

---

