---
title: "xgamma in startup does not persist"
date: 2013-11-02
forum: General Help
---

### Post by samwillc on 2013-11-02
Hi, running Ubuntu 12.04 on an older desktop and needed to lower xgamma in order to match my macbook which I also use on this same screen. Macbook connected via DVI and desktop via HDMI, I just change the source to use each system.

Anyway, I have added:

/usr/bin/xgamma -gamma 0.3

to the startup applications. However, each reboot, the settings are used for a few seconds, then the screen reverts back to being setting 1.0 i.e. too bright. Why is this not persisting? Every other thread I'e read says this is the way to achieve this. Any help is very appreciated, thanks.

**EDIT**

So I read this post:

[http://ubuntuforums.org/showthread.php?t=1956897](http://ubuntuforums.org/showthread.php?t=1956897)

and made a shell script thus:

[FONT=courier new]#!/bin/sh
sleep 10 #delay run
/usr/bin/xgamma -gamma 0.3 #change screen gamma on startup[/FONT]

and put this in home/Sam/changeGamma.sh

and right clicked the file and made it executable,  This works ok, using 0.3 to make the change obvious to the eye, will actually use 0.8.

I have 2 questions though:

1) Without the sleep, my settings are applied and then overwritten back to 1.0. What would cause this?
2) Putting a script in 'home', does this mean 'home/Sam', or 'home' which contains the folder Sam. I have two home folders so a bit confused. Is the correct path:

home/Sam/changeGamma.sh OR
home/changeGamma.sh

Or is this the same thing, I am the only user.

Thanks.

**EDIT 2**

Also tried removing my script from startup, then:

[FONT=courier new]gksu gedit /etc/lightdm/lightdm.conf[/FONT]

and added:

[FONT=courier new]session-setup-script=/usr/bin/xgamma -gamma 0.3[/FONT]

to the bottom. Same thing, settings were applied on restart (woohoo), then a couple of seconds later, back to 1.0 (sigh).

---

### Post by samwillc on 2013-11-02
FACEPALM...

Dash > Nvidia X Server settings > gamma level? Set to 1 of course! Didn't think the open source drivers would offer such functionality. I'll remember this next time.

---

### Post by Toz on 2013-11-02
> 2) Putting a script in 'home', does this mean 'home/Sam', or 'home' which contains the folder Sam. I have two home folders so a bit confused. Is the correct path:

home/Sam/changeGamma.sh OR
home/changeGamma.sh
I would recommend creating a bin directory in your home directory (/home/Sam/bin) and putting all your scripts in there. The reason is that by default, the a bin directory is added to your path. Try:
```
echo $PATH
```
...or in ~/.bashrc:
> PATH=$PATH:~/bin


---

### Post by samwillc on 2013-11-02
> **Toz said:**
> ```
echo $PATH
```

Hi, thanks. The above gives me this:

```

/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

```

lightdm is in my path? Maybe this happened when I attempted that step above and edited the conf file or possiby from when I changed nvidia settings? Seems a bit weird having that in there.

---

