---
title: "A few apt-get questions"
date: 2007-07-07
forum: General Help
---

### Post by highenergy on 2007-07-07
Hello,

I have a few questions related apt-get;

1-) How can I update only a specific application for example xmms ? Is there something similar to "apt-get update xmms" ?

2-) How do I search repository from command line? For example I want to search a file in repository and if it's available I want to check it's version number too. So that I decide whether or not to install it. Is there an apt-get command to to that?

3-) For example I want to update only applications. I don't want security and system updates. How can I do that using apt-get.

4-) Uhm, this last question is out of the subject. When I first run mplayer it gives me an error, a video driver error. I change video driver from it's options menu among many drivers to xv or something similar to that I don't remember exactly it's name right now. Then it begins to work. Can anyone explain which video driver is the best and why there are such more video drivers in the options?


regards
H.E
:p

---

### Post by Happy_Man on 2007-07-07
1. Not sure..... read the man page for apt-get. ```
man apt-get
```

2. I believe the command is ```
apt-cache search <programname>
``` Don't quote me on that, as I'm not sure that's it.

3. Don't think you can for obvious reasons.

4. I don't get what you're asking. Can you be more specific?

---

### Post by darkdigger on 2007-07-07
If you have the restricted drivers installed, I would recommend using the gl driver (X11 OpenGL). I've never tried gl2, so it might be better. In my experience large videos seem to render faster and not take up as much CPU time when using the gl driver (versus xv).

If you want to search for available packages use 
```
apt-cache search *searchString*
```

I would recommend filtering the results with a '| grep' after the 'apt-cache' because I think apt-cache tries to match the entire string (spaces and all) instead of matching words like iTunes.

---

