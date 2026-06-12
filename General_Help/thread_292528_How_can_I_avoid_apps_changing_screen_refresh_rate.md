---
title: "How can I avoid apps changing screen refresh rate?"
date: 2006-11-03
forum: General Help
---

### Post by hexion on 2006-11-03
Hi.. some doubts here :mrgreen:

This happened in dapper and now in edgy too, and I've not been able to solve it yet.

I have a TFT. With Ubuntu, I see the fonts clearer with 60 hz than in 75 hz :-k

Well, screen configured to stay at 60 hz. But, my problem comes sometimes when I play games (like enemy territory) in fullscreen.

When I close the game, refresh rate is set in 75 hz (the higher rate avaiable).

Any ideas on how to "freeze" that option?
Any file to edit? (so I can make an script to set it to 60 hz when it's changed) I didn't see any option in xorg.conf related to the refresh rate...


Thanks in advance

---

### Post by dcstar on 2006-11-03
> **hexion said:**
> 
.......
Any file to edit? (so I can make an script to set it to 60 hz when it's changed) I didn't see any option in xorg.conf related to the refresh rate...


Thanks in advance

There aren't any options because the default override is not set, if you do:
```
sudo dpkg-reconfigure xserver-xorg
```
There will be a section on setting refresh rates, you can then lock yours to only use 60Hz (if you like). The xorg.conf file will then have an entry.

You may have to run the command a few times to get it set 100% right, the old xorg.conf file will be renamed in case you need it.

---

### Post by hexion on 2006-11-04
Ok, I'll try that command.
Thanks for your help ;)

---

### Post by wijet on 2006-11-04
I have similary problem. I can't change refresh rate .I want 60Hz, I have 75Hz on my LCD. In  
```
sudo dpkg-reconfigure xserver-xorg
```
i set 1260x1024 @ 60Hz ,
also change manualy xorg.conf HorizSync and VertFerfesh, But in kcontrol only option is 75Hz.

---

