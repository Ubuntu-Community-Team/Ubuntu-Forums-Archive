---
title: "ATI Drivers under Ubuntu Breezy won't work"
date: 2005-10-28
forum: General Help
---

### Post by =Kevin= on 2005-10-28
First of all, hi!

I've browsed the forum for quite a while now, and decided to join the fun :cool: 
I'm kinda new to Linux, i had some other installations before (Ubuntu Hoary,Gentoo,Mandrake), but i couldn't ever install Games with Cedega.
I now switched to Ubuntu Breezy 5.10 (KDE) and i'm very pleased with it.
I successfully installed some games with Cedega!:D 

But now, the problem is i can't install the ATI drivers, on other distro's i could 
install the drivers for ATI but couldn't install the Games :???: 
I don't remember how i did it on the other ones, that's why i' m asking for help.
I've tried the guide here on the forum for the new ATI driver (8.18 or so) and when i tried glxgears it would display them at very low fps and an error in console about 
" Xlib:  extension "XFree86-DRI" missing on display ":0.0".
X connection to :0.0 broken (explicit kill or server shutdown)." 

I've also tried other guides but none of them seem to be working.
I' m using the latest Ubuntu Breezy with KDE + kernel 2.6.12-9-386.

I've come so far now that i can even install games (wow :eek:) but now i' m stuck at the ATI drivers. I really wanna make this my main distro (i haven't got a windows dualboot) and i'm really enjoying Linux!!

Any help would be very appreciated!
If you would like to, you could also add me on MSN, it's easier to talk like that.
Address is  kevinvanrooij [at] gmail [dot] com

Cheers!
Kevin

**EDIT** Gosh i feel dumb, i forgot to replace "ati"  in xorg.conf with " fglrx"! I've did that now, and the strange error about Xlib (see above) doesn't appear anymore. But now with glxgears it goes really really slow (like first) and doesn't display FPS in console. If i close the glxgears then this is written in console: "X connection to :0.0 broken (explicit kill or server shutdown)" 
My fglrxinfo is this:
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

I'm stuck.......again :(

---

### Post by soonindallas on 2005-10-28
[QUOTE==Kevin=]
My fglrxinfo is this:
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

I'm stuck.......again :([/QUOTE]

Hi.  this means your install of the drivers or module was unsuccessful or your x is not set up properly.  I don't know which and I suspect you and I have about the same level of linux sophistication.  I wanted my ATI card 3D acceleration to just work.

I also had a bunch of problems, and the same symptoms as you with my radeon mobility 9700.  I followed these instructions [http://ubuntuforums.org/showthread.php?t=75428](http://ubuntuforums.org/showthread.php?t=75428) and 3D acceleration worked.

I have to say that I had followed the instructions in a bunch of other threads without success before looking at this one.  to be honest its simplicity appealed to me and it worked!

Once you get it working I would suggest you don't get in a pissing contest regarding the fps you get with glxgears (you even have to run it with a verylongdisclaimeracknowledgingglxgearsisnotabenchmark option to get it to display fps now) just run your games in 3D!

---

### Post by =Kevin= on 2005-10-28
EDIT 
Oh, i just noticed, i followed that guide already and it didn't work....oops
But thanks anyway!

---

### Post by soonindallas on 2005-10-28
ok.  good luck.

I honestly cannot say how the method I used to get it working differs from the half-dozen others I tried unsuccessfully.  Nor can I guarantee that this method is complete: maybe it only worked because I had some other package configuration after trying the instructions in a different thread.

It is frustrating though that when you have this problem and you do a search on the forum for "ati fglrx driver" or some such you find 200 threads some of which have several hundred messages in them.  It is indicative of the difficulty af getting Linux to work with these ATI cards.

---

### Post by =Kevin= on 2005-10-28
Yup it really is frustrating to get ATI to work under Linux..
I wish i had kept those notes where i wrote how to install them....:(

---

### Post by mindwarp on 2005-10-28
Ok actually I had the same error, and the drivers are easy to install.  The error comes from you not properly removing linux-modules-restricted.  Refollow the guide, using that step, and you will have proper acceleration.  Also glxgears no longer displays FPS without the proper command switch (-iacknowledgethatthistoolisnotabenchmark)

---

### Post by =Kevin= on 2005-10-28
Thanks alot, i' ll try this right away too!

---

### Post by mangoshake on 2005-10-28
```
glxgears -iacknowledgethatthistoolisnotabenchmark
```

is cute, but if you tend to get typos when you type (like me), you could use a shorter command switch:
```
glxgears -printfps
```

---

### Post by =Kevin= on 2005-10-28
Still doesn't work, even after i removed the restricted modules....
i' m getting so tired of this, i can finally install my games but now ATI won;t work!! :(

*cries for help*

---

### Post by =Kevin= on 2005-10-28
FINALLY IT WORKED!!!!!!!! :D

For other people people, this is what i did: [http://ubuntuforums.org/showthread.php?p=423589](http://ubuntuforums.org/showthread.php?p=423589)

Thanks alot mlomker(maker of that guide) and the people here that tried to help me!

:D

---

### Post by mindwarp on 2005-10-28
Ah there were a couple of guides floating around, that is the one I used also.  Glad you got it working

---

