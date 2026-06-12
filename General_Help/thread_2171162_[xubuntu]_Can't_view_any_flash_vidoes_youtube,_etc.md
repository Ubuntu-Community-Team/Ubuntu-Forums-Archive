---
title: "[xubuntu] Can't view any flash vidoes youtube, etc."
date: 2013-08-29
forum: General Help
---

### Post by vikram_kapoor on 2013-08-29
I have installed the flash player by the following command:
```
sudo apt-get install flashplugin-installer
```

After that I open up youtube to find that my videos are not displaying correctly, please see the screens below:

Youtube:

[IMG]http://imageshack.us/a/img405/991/a14o.png[/IMG]

Dailymotion:

[IMG]http://imageshack.us/a/img15/1725/xv3e.png[/IMG]


I have failed to understand where the problem is. I am running xubuntu 13.04 (latest i guess), and all the latest updates are installed. Anyone encountered this before ? Any help please ?
Thanks.

---

### Post by GwL3eNC on 2013-08-29
I saw in another forum that deactivation of the hardware acceleration in the flash player settings
solve the problem. Also some people removed &#314;ibvdpau1 package to solve the problem.

---

### Post by vikram_kapoor on 2013-08-30
[**[COLOR=#000000]@GwL3eNC- [/COLOR]**[COLOR=#000000]Tried disabling hw acceleration, didn't work.[/COLOR]]("http://ubuntuforums.org/member.php?u=1841512") And I couldn't figure out how to remove &#314;ibvdpau1 package :(

---

### Post by GwL3eNC on 2013-08-30
Hey,

with

sudo dpkg -l | grep &#314;ibvdpau1

you can find if the package is installed on your system. If so a

sudo apt-get remove &#314;ibvdpau1

should remove the package. I hope this is right for your problem, because
the german guys speak about wrong colors. I'm not shure this describes your
problem. Please check also your graphic settings, some people find out
a wrong setting causes the trouble.

---

### Post by vikram_kapoor on 2013-09-03
> **GwL3eNC said:**
> Hey,

with

sudo dpkg -l | grep &#314;ibvdpau1

you can find if the package is installed on your system. If so a

sudo apt-get remove &#314;ibvdpau1

should remove the package. I hope this is right for your problem, because
the german guys speak about wrong colors. I'm not shure this describes your
problem. Please check also your graphic settings, some people find out
a wrong setting causes the trouble.


**E: Unable to locate package &#314;ibvdpau1**

---

### Post by GwL3eNC on 2013-09-03
Hello vikram,

my last idea. unistall flash

sudo apt-get purge flashplugin-installer

and the choose adobe-flashplugin 

sudo apt-get install adobe-flashplugin 

That it was. i dont have any another idea.

---

### Post by vikram_kapoor on 2013-09-03
> **GwL3eNC said:**
> Hello vikram,my last idea. unistall flashsudo apt-get purge flashplugin-installerand the choose adobe-flashplugin sudo apt-get install adobe-flashplugin That it was. i dont have any another idea.E: Package 'adobe-flashplugin' has no installation candidate

Its all right mate, thanks for all the help. All the companies are against open source I guess.

---

### Post by mastablasta on 2013-09-03
you need to enable all repositories. adobe is in partner repositories i think. just go to software sources, enable repositories then it will appear in software center after you update it (same for apt-get command).

easiest way is to simply install ubuntu-restricted-extras package. it comes with a lot of usefull and necessary stuff, especially if you play audio and video.

if it still doesnt' work then install google Chrome (not the opensource Chromium) using their .deb file or i believe there is also a PPA available. it comes with it's own flash.

---

### Post by tripp98 on 2013-09-03
Why not try it the simple way.

software center
xubuntu restricted extras

---

### Post by vikram_kapoor on 2013-09-05
> **mastablasta said:**
> you need to enable all repositories. adobe is in partner repositories i think. just go to software sources, enable repositories then it will appear in software center after you update it (same for apt-get command).

easiest way is to simply install ubuntu-restricted-extras package. it comes with a lot of usefull and necessary stuff, especially if you play audio and video.

if it still doesnt' work then install google Chrome (not the opensource Chromium) using their .deb file or i believe there is also a PPA available. it comes with it's own flash.

Yes! Yes! Yes! :guitar: Google Chrome did the trick, and I always thought that Chrome and Chromium were the same. Thanks mastablasta :KS

---

