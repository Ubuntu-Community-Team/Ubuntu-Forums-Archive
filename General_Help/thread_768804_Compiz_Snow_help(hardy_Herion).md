---
title: "Compiz Snow help(hardy Herion)"
date: 2008-04-26
forum: General Help
---

### Post by Twitch6000 on 2008-04-26
Well On gusty after a few searchs I got snow installed in a snap.On hardy I did just like I did on gusty and no luck.It says I am missing files and such.So I download them and still no luck.So can someone give me a how to to install the snow effect on compiz for hardy.

Another question is for awn.
I cannot get the curves to install cause of a file not being able to be installed or even found.Is there a new way to get curves for hardy?

---

### Post by Creptic on 2008-04-26
You may want to try compiz-git to get the extra plugins to work. Here is a link 

[http://ubuntuforums.org/showthread.php?t=763829&highlight=git-compiz](http://ubuntuforums.org/showthread.php?t=763829&highlight=git-compiz)

---

### Post by Twitch6000 on 2008-04-26
I don't want to do that I just want to use my compiz that comes with hardy and add the plugin.I know its possible(atleast it was with gusty).

---

### Post by Twitch6000 on 2008-04-27
Bump
Anyone got any other ideas?
I thought this would be easy =[.

---

### Post by Twitch6000 on 2008-04-28
ok I got the snow but, I still have not got the awn curves any help on that?

---

### Post by Kaneda187 on 2008-05-24
how'd you get the snow to work??

---

### Post by Tekovro on 2008-07-15
> **Twitch6000 said:**
> ok I got the snow but, I still have not got the awn curves any help on that?

please tell us how you got it to work. i want snow!!

---

### Post by anubis3000bc on 2008-10-11
How did you get snow to work,i have all my old compiz files saved from gusty and used them when i upgraded i had no problems but some plugins are not there anymore like snow and freewins etc....so let me know how you got snow to work.

---

### Post by xjgnsdof on 2009-01-01
In Hardy, do the following:

```
sudo apt-get install compiz-bcop compiz-dev compizconfig-settings-manager build-essential libtool libglu1-mesa-dev libxss-dev libcairo2-dev git-core
```
```
mkdir -p  ~/compiz/
```
```
cd ~/compiz
```
```
git clone git://anongit.compiz-fusion.org/fusion/plugins/snow
```
```
wget -O /tmp/snow.tar 'http://oreaus.googlepages.com/snow.tar'
```
```
mkdir -p ~/compiz/
```
```
tar -xf '/tmp/snow.tar' -C ~/compiz/
```
```
cd ~/compiz/snow
```
```
make clean
```
```
make
```
```
make install
```

I hate when people say that they've solved their own problem and don't say how they did it. Greedy...

---

### Post by anubis3000bc on 2009-01-01
Nice i got snow to work and freewins i love ubuntu hardy haron.

---

### Post by caveman59330 on 2009-05-02
I installed all of the dependencies and when I go to System Preferences Advanced Desktop Effects Settings and open compiz fusion I see the snow plugin but If I put a check in the box to use it it will disappear by itself all of a sudden no checlmark to use snow effects.

---

### Post by anubis3000bc on 2009-05-02
Yeah i was using ubuntu 9.04 for awhile and i found that when upgrading from 8.10 the compiz files got mixed up so gfconfig files in compiz the plug ins wont work when set to that file backend so i switched to flat file backend and some of the plugins that didn't work. I was able to use some plugins but not all, so what i did was reinstalled my ubuntu 8.10 and all my plugins worked correctly.

---

### Post by moonsoup on 2009-12-15
WOW! I come here looking for help with something... 
I see several people who are willing to help and this is good.
However, I am ultra disappointed when the person who started the thread won't help others by providing a solution. Deplorable!
Community input is the only thing really making this whole system of 
software work in the first place.
Hey, Twitch6000! What is that! You ask for help and even send a bump and then don't help back!?!?!? Bad Twitch! OUCH!
Man! I am going to start checking peoples input before I help them.
Just plain wrong.

CONTRIBUTE PEOPLE ! ! !

---

### Post by anubis3000bc on 2009-12-21
Man it's been years since i been to this site what's cracking people?

---

### Post by Don Scapp on 2010-02-06
[https://launchpad.net/ubuntu/karmic/i386/compiz-fusion-plugins-unsupported/0.8.3+git20090911-1ubuntu1](https://launchpad.net/ubuntu/karmic/i386/compiz-fusion-plugins-unsupported/0.8.3+git20090911-1ubuntu1)

The build worked for me!

---

