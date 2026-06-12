---
title: "need help with video card"
date: 2006-11-24
forum: General Help
---

### Post by Mike322 on 2006-11-24
im trying to install a nvidia XfX 6800 XT agp with 256 mb gddr3 i can view perfectly without the driver configured in X when i try to configure it and load DRI and GL core on my module section it only shows DRI but no GL core so i tried loading with only DRI and switching the driver name to nvidia and no luck idk wtf is wrong i got the latest driver followed all the instructions any suggestions? i was thinking about putting in a older video card a nvidia MX440 128 mb ddr but i want to run XGL + compiz so maybe that card wont perform good please help im a complete noob and htis is only the video card part of my problem i have no sound somebody please help me ](*,)

---

### Post by po0f on 2006-11-24
Mike322,

Slow down.  Use punctuation.  It makes it hard to read the post and help you, and quite frankly, I don't take posts like the above very seriously.

Which guide did you follow to install your NVIDIA drivers?  Also, if you can't even get the drivers installed, I don't believe Compiz is for you, as it's a more complicated process.

---

### Post by Mike322 on 2006-11-24
sry im just so used to typing like this....well i used the [method shown here]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper") i used method 1 offline installation...right when i get to that part where you gotta put the # in fron of the module's i get only DRI but no GLcore...should i jsut try another video card my MX440 128 mb ddr or just see if i get a good response?

---

### Post by po0f on 2006-11-24
Mike322,

I believe that the guide you followed has a couple of typos.  Posted below are my "Module" and "Device" sections from my xorg.conf.  I also use an NVIDIA card.
```
Section "Module"
    Load "i2c"
    Load "bitmap"
    Load "ddc"
#   Load "dri"
    Load "extmod"
    Load "freetype"
    Load "glx"
    Load "int10"
    Load "type1"
    Load "vbe"
EndSection

Section "Device"
    Identifier "VideoCard0"
    Driver     "nvidia"
EndSection
```

I didn't have a load module line for "glcore", but I'm using Edgy.

---

### Post by CatKiller on 2006-11-24
The "GLcore" module gets removed from the xorg.conf by nVidia's setup anyway. As does "dri" for that matter.

Since those lines need to be either removed, or commented out by putting the # at the beginning of the line, it doesn't matter if they are there or not. Either way you're going to make it so that the module doesn't get loaded.

---

