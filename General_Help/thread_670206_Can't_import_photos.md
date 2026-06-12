---
title: "Can't import photos"
date: 2008-01-17
forum: General Help
---

### Post by JaggedOne on 2008-01-17
I was previously running ubuntu on this laptop. When I plugged in my iPhone or my girlfriends digital camera, a little box would pop up to let me import photos. It worked great. I recently switched to Mint. Ever since then whenever I plug in either of the cameras, the same box shows up. However when I click import, nothing happens. The box just goes away and no pictures are imported. 

Any ideas?

---

### Post by Mostlyharmless42 on 2008-01-20
I have the exact same problem....please help

---

### Post by lluisanunez on 2008-01-20
Where does the camera mount in? In Ubuntu it's /media/blah blah... Maybe now it's being mounted in a different place, like /dev/blah blah ?

---

### Post by Mostlyharmless42 on 2008-01-20
that's the thing, i can't seem to find it mounted anywhere.  I only did this once or twice on ubuntu, so i can't remember where it's suposed to be.  All i know is it's not in /media or /dev

Anyone know where my camera could be mounted???

PS-Picassa can't detect it either, and the camera is a Canon S2 IS

---

### Post by Mostlyharmless42 on 2008-01-20
After searching for a bit on the Mint forums i found out that the problem is that Mint doesn't come w/ gThumb image viewer.  The dialog still exists, but there is no program that can import photos.  gThumb is also the program that installs the drivers for your camera.  Before it does this, your camera can't be mounted.  So the solution is really simple...install gThumb with this code

```
sudo apt-get install gthumb
```

P.S. 
This thread should be marked [SOLVED]...i'm not sure how to do that.

---

### Post by lluisanunez on 2008-01-20
Never thought of that!

There is an even simpler solution: System > Preferences > Removable drives and media > Cameras (uncheck the "import photos" option)

:-)

*This thread should be marked [SOLVED]...i'm not sure how to do that.*
Go to the top Thread tools > Mark as solved

---

