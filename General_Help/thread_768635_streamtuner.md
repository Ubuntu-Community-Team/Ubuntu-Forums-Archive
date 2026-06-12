---
title: "streamtuner"
date: 2008-04-26
forum: General Help
---

### Post by Tucatts on 2008-04-26
Good morning all. Have installed Hardy and with a few minor bugs I am pretty happy. Printer and scanner worked right off, compiz works and will try the fusion icon to load it after boot up. Music plays, video plays, streaming video on web sites plays. I am dual booted with XP on a system I built about 4 years ago, P4 2.5, 1.75 ram, 5500 nvidia card soon to be replaced with a 6600 card with a heat sink. Fan quit on the 5500, sounded like a lawnmower! have the same bugs with Firefox but that will be fixed soon so no problem, I always install Epiphany anyway along with Firefox. SO what's not to like! LOL. 
Where the heck is xmms? I can't get streamtuner to work without it. Have installed xmms2 but to no effect. Any ideas?
Thanks!

---

### Post by ryanhaigh on 2008-04-26
It has been a while since I used this app but can you not change the media player preference to somethig other than xmms such as totem. If not then what about creating a symlink from /usr/bin/xmms to /usr/bin/totem (no idea if this will work but may be worth a shot as according to bug reports streamtuner isn't being actively developed anymore)
```

sudo ln -s /usr/bin/xmms /usr/bin/totem

```

---

### Post by Tucatts on 2008-04-26
Ok, thanks, will give it a shot. Actually Rhythmbox plays streaming radio just fine but just have gotten used to streamtuner and it always worked so well. Sorry to hear that it is not being updated anymore. Thanks again!

---

### Post by TryMe on 2008-04-26
Best solution I have found is to install audacious. Then open up ~/.streamtuner/config in gedit. Do a find and replace for xmms replace with audacious. Save changes.

Everything just works after that.

---

### Post by natrixgli on 2008-04-26
Agreed! Audacious is great. If you go into the Streamtuner preferences, under 'applications' you can just replace 'xmms %q' with 'audacious %q'



Cheers,

-n8

---

### Post by anjilslaire on 2008-04-27
Check this thread for a deb of xmms that works great!

[http://ubuntuforums.org/showthread.php?t=765609&highlight=xmms+hardy+streamtuner]("http://ubuntuforums.org/showthread.php?t=765609&highlight=xmms+hardy+streamtuner")

---

### Post by Tucatts on 2008-04-27
Hey THANKS, listening to some "oldies" on streamtuner right now, LOL. Audacious works great. Just going to preferences like you said Natrixgli and making the change to audacious worked like a charm. If I can get Hardy to quit freezing up I will be set, ha ha.
Thanks again for everyones posts. Great community!

---

