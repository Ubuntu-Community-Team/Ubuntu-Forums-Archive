---
title: "Screen resolution increase!"
date: 2007-06-30
forum: General Help
---

### Post by logreeval on 2007-06-30
i cant get past 1024x768 i have tried modifying the files, i just put it back to the default file.

can you guys help me get to 1280x800? please :)

thank you

---

### Post by mouseboyx on 2007-06-30
```
sudo gedit /etc/X11/xorg.conf
```add a mode

so it looks like this

donotcopypaste<(

```
SubSection "Display"
        Depth    24
        Modes        "1280x800"    "1024x768"    "800x600"    "720x400"    "640x480"
    EndSubSection
```)>donotcopypaste

my monitor is so old it doesn't go past 1024x768 or it will get messed up so that might be the case with you.

---

### Post by logreeval on 2007-06-30
i did that and nothing happens :(

btw, i checked and the max resolution is 1280 x 800

i dont know how to fix this :(

---

### Post by confused57 on 2007-06-30
> **logreeval said:**
> i did that and nothing happens :(

btw, i checked and the max resolution is 1280 x 800

i dont know how to fix this :(
What kind of video card do you have?  Ubuntu may have defaulted to the "vesa" driver, which works, but is limited in it's display capabilities.

---

### Post by CocoAUS on 2007-06-30
Try [http://erusan.googlepages.com/ubuntuhowto.html#resolution](http://erusan.googlepages.com/ubuntuhowto.html#resolution)

Essentially, just add your resolution AND your refresh rate, then restart X.

---

### Post by DrEmpire on 2007-06-30
i got lots of help in my post about screen resolotion check this out it may help

[http://ubuntuforums.org/showthread.php?t=486844&highlight=screen](http://ubuntuforums.org/showthread.php?t=486844&highlight=screen)

---

### Post by logreeval on 2007-06-30
EDIT: I GOT IT!!!

If you have an integrated intel graphics card, use **915resolution** install it from synaptic

---

### Post by aen on 2007-07-26
> **CocoAUS said:**
> Try [http://erusan.googlepages.com/ubuntuhowto.html#resolution](http://erusan.googlepages.com/ubuntuhowto.html#resolution)

Essentially, just add your resolution AND your refresh rate, then restart X.

The link above is by far the fastest and best solution for the many many monitors I've done it on.

---

