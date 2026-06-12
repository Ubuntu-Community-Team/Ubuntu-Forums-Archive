---
title: "Repair Xserver?"
date: 2007-08-10
forum: General Help
---

### Post by Trifid on 2007-08-10
I have a old Dell GX50 which wouldn't boot of the Xubuntu livecd (same as Ubuntu, but this gave me the splash screen to chose modes). 

Anyway to cut a long story short I installed Xubuntu on my main PC (with 7800GT) onto the harddrive and put it in the GX50. Now it boots fine, giving me the Xserver error, then into CLI where I want a quick nod.

Will following this guide fix the problem? [http://ubuntuforums.org/showthread.php?t=241254](http://ubuntuforums.org/showthread.php?t=241254)

Looking forward to finally having a server. :)

Thanks, Trif.

---

### Post by forestpixie on 2007-08-10
-did you read the last post - that's an old bug - you sure that's what you need. If you haven't got the xserver - I guess that's because you installed not only with a different pc but a different graphic card - is that right?

have you not tried to reconfigure the xserver? This is the command but have a search to make sure it's what you need to do :)

sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by Trifid on 2007-08-10
No. I had to go to work. I believe I have used that before. It gives me quite a few Q's about the graphics card i.e. VRAM?

Completely different systems. The only thing they shared in common was the hard drive for 15mins during install. I really need to reinstall the graphics drivers. Was hoping it was going to be plug in and work but this is why I waited so long for a system I can mess about on. :D

---

### Post by forestpixie on 2007-08-10
I think you need to read the questions but basically i let most default. you can run it without -phigh I believe it asks less questions but not sure never having done it.

What sort of graphics card is it?

I'd go for the reconfig - so's at least you can get in. I know for nvidia (at least for me :) ) you can get close with the restricted drivers in system >admin

---

### Post by Trifid on 2007-08-10
It has a Intel i810.

I'm home now, just need to eat lunch and I will start!

---

### Post by forestpixie on 2007-08-10
enjoy lunch - once you've got the xserver reconfigured there's a whole bunch of stuff on i810 driver

there's a [howto]("http://ubuntuforums.org/showthread.php?t=27029")

and this fairly abrupt [one]("http://ubuntuforums.org/showthread.php?t=324736")

this is the search I used 

[http://ubuntuforums.org/search.php?searchid=25178412](http://ubuntuforums.org/search.php?searchid=25178412)

I saw this in one of them

> **PriceChild said:**
> You'll have to ensure that your X server is configured correctly...
```
sudo dpkg-reconfigure xserver-xorg
```and choose i810 when you have to choose the driver.

Leave everything else as defaults!

so try with that reconfigure instead of the -phigh one 

Good luck :)

Edit - just checked on mine and the i810 package is installed - I didn't do it - so I guess it comes with the install

---

### Post by Trifid on 2007-08-10
Thanks for your help. I am now in the GUI. :D When I go into terminal it just restarts to the login screen. Not too sure why thats happening. I am in the fail safe terminal one now to get those drivers and a decent refresh rate (and res).

---

### Post by splintercellguy on 2007-08-10
Oh, that's a bug in the Terminal itself. You have to edit xorg.conf so the depth is 16-bits. You can press Alt-F2 and type xterm if you require a terminal.

---

### Post by forestpixie on 2007-08-10
Good - glad I could help - re the terminal thing I've no idea how to deal with that but I did see something similar recently on the forums. :) I'll see if I can find it though

Edit - no I won't :)

---

### Post by Trifid on 2007-08-10
Its not too great of a problem. Hopefully by tongiht/early saturday I should be able to stick the PC in the cupboard headless. :D

---

