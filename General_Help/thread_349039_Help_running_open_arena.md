---
title: "Help running open arena?"
date: 2007-01-29
forum: General Help
---

### Post by thegreenblob on 2007-01-29
Ok, I installed the .deb package of open arena and I go to start it and it just starts up for a split second then closes :confused: .

Any idea on what could be wrong?

I got the windows version working in wine but goes very slow.

(Open Arena - [http://openarena.ws](http://openarena.ws)) (Installed Deb Package - [http://www.getdeb.net/category.php?id=1&release=Edgy](http://www.getdeb.net/category.php?id=1&release=Edgy) somewhere in there)

Any help?

---

### Post by scrooge_74 on 2007-01-29
I am not sure what is the problem? How did you went about installing, I used the package from Synaptic and have been having fun for a couple of weeks now.

---

### Post by thegreenblob on 2007-01-29
Basically, I start up the game, then it automatically shuts down the game like 3 secs after it pops up. I don't even get in the game really.

And I don't really know why its doing it which is why I came here, lol.

---

### Post by scrooge_74 on 2007-01-29
Video card settings? Do you have 3D enable?

---

### Post by thegreenblob on 2007-01-29
Uhhh... I have no idea, lol. How would I find out? I play this game under windows alot so it works there... but I'm trying to switch to ubuntu so I'm trying to get it to work here.

---

### Post by scrooge_74 on 2007-01-29
What video card you have? this is important

do this command on a terminal window glxinfo | grep direct

the system will tell you if you have or not 3D capability

---

### Post by thegreenblob on 2007-01-30
Ok, it says I have a...

direct rendering: No
OpenGL renderer string: Mesa GLX Indirect

And my video card is a ATI RADEON XPRESS 200M IGP.

So any more help?

---

### Post by thegreenblob on 2007-01-30
Ok... I did some googling and manages to get it started by running it from the command line using - "/usr/share/openarena/ioquake3.i386 codered +set r_gldriver libGL.so.1 +set r_allowSoftwareGL 1". And it runs but EXTREMLY SLOW... even the windows version using wine is faster... pleas help someone! I don't wanna reboot any time I wanna play this game!

---

### Post by scrooge_74 on 2007-01-30
> **thegreenblob said:**
> Ok, it says I have a...

direct rendering: No
OpenGL renderer string: Mesa GLX Indirect

And my video card is a ATI RADEON XPRESS 200M IGP.

So any more help?

Your problems will be solve once you installed 3D drivers for your card, that is the reason is running so slow.

Check this [website]("http://albertomilone.com/nvidia_scripts1.html") and follow instructions to get the correct drivers for your card.

Let me know if you dont understand something, I have an Nvidia card but the end resull is the same, my Open Arena has very good speed for a laptop which only has 256 RAM

---

### Post by thegreenblob on 2007-01-30
Ok... I don't get it. I ran it from the command line and pressed the number to install a ati driver... and it just took me to a black screen and did nothing. Was I supposed to do something there? Or did I do something wrong?

---

### Post by scrooge_74 on 2007-01-30
Did you enable the other repositories?

---

### Post by thegreenblob on 2007-01-30
uhh... Sorry I have no clue what you mean, lol.

*is a linux newb*

So... how would I do this?

---

### Post by scrooge_74 on 2007-01-30
You should read again the instructions and check the link there for adding repositories [http://www.monkeyblog.org/ubuntu/installing/#enabling_extra_repositories](http://www.monkeyblog.org/ubuntu/installing/#enabling_extra_repositories)

---

### Post by thegreenblob on 2007-01-30
Ok, they are enabled. It does the same thing :/

---

### Post by scrooge_74 on 2007-01-30
Ok, you should talk to the expert on this matter, go and check this [thread]("http://www.ubuntuforums.org/showthread.php?t=255929")

---

