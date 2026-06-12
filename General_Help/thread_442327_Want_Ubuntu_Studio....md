---
title: "Want Ubuntu Studio..."
date: 2007-05-13
forum: General Help
---

### Post by Fireblend on 2007-05-13
...but I'm too busy/lazy to backup all my data right now. Is there some way I can install Ubuntu Studio without having to do all of this? Like installing all applications/theme etc... over my current 7.04 install? It looks too awesome... and I've tried some of the apps it comes with... I definitely want it :(

---

### Post by Patrick-Ruff on 2007-05-13
for some reason their website isn't working for me . . .there might be some way.  only way you can find out is to burn the cd and pop it in.

---

### Post by richbiskit on 2007-05-13
i upgrded my 7.04 by adding the ubuntu studio repositories to my source list then going into synaptic and istalling the ubuntu studio desktop and all the ubuntu studio packages, it took about 20mins and works perfectly. :)  see below... (provided by SD-Plissken)

On their site it list these two commands

Command one:
sudo su -c 'echo deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main >> /etc/apt/sources.list'

Command Two:
wget -q [http://archive.ubuntustudio.org/ubuntustudio.gpg](http://archive.ubuntustudio.org/ubuntustudio.gpg) -O- | sudo apt-key add - && sudo apt-get update

Next step open synaptic, and do a search for these files.

# ubuntustudio-desktop
# ubuntustudio-audio
# ubuntustudio-audio-plugins
# ubuntustudio-graphics
# ubuntustudio-video
# ubuntustudio-artwork
# ubuntustudio-gdm-theme
# ubuntustudio-icon-theme
# ubuntustudio-look
# ubuntustudio-session-splashes
# ubuntustudio-sounds
# ubuntustudio-screensaver
# ubuntustudio-theme
# ubuntustudio-wallpapers
# usplash-theme-ubuntustudio
# wired

---

### Post by ep2011 on 2007-05-13
> **richbiskit said:**
> 
Next step open synaptic, and do a search for these files.

# ubuntustudio-desktop
# ubuntustudio-audio
# ubuntustudio-audio-plugins
# ubuntustudio-graphics
# ubuntustudio-video
# ubuntustudio-artwork
# ubuntustudio-gdm-theme
# ubuntustudio-icon-theme
# ubuntustudio-look
# ubuntustudio-session-splashes
# ubuntustudio-sounds
# ubuntustudio-screensaver
# ubuntustudio-theme
# ubuntustudio-wallpapers
# usplash-theme-ubuntustudio
# wired

In my opinion it would probably be better to use aptitude (ex, sudo aptitude install ubuntustudio-desktop ubuntustudio-auto ...)

With aptitude, if you need to uninstall (sudo aptitude uninstall ...), it works a little bit better and uninstalls EVERYTHING, whereas apt-get and synaptic sometimes leaves some things installed.

---

### Post by kystorms on 2007-05-13
so, can one run studio "with" feisty or does it have to be a new install all together?
I would love to play around with it, however I just completed getting Fiesty exactly to my liking, so I would hate to lose my stuff

---

### Post by Buffalo Soldier on 2007-05-14
> **ep2011 said:**
> In my opinion it would probably be better to use aptitude (ex, sudo aptitude install ubuntustudio-desktop ubuntustudio-auto ...)

With aptitude, if you need to uninstall (sudo aptitude uninstall ...), it works a little bit better and uninstalls EVERYTHING, whereas apt-get and synaptic sometimes leaves some things installed.

That would be true for old versions of apt-get. With newer version of apt-get all you need to do to remove "orphaned" packages is:```
sudo apt-get autoremove --purge
```

---

### Post by mooscape on 2007-05-19
No need to download the DVD.  Check out : [http://www.ubustu.com/](http://www.ubustu.com/) .  I upgraded from Feisty with no problems -so far :) .

 :idea: Idea: Can't the download be stuck on two CD's rather, for us poor proletariate that can't afford DVD burners.

---

### Post by stereo3D on 2007-05-19
The solutions suggested sound good for installing the software and eye candy, but isn't the core of Ubuntu Studio different? It is described as "low latency," reducing the lag time between the OS and the CPU. I think that might be critical for some real time processing of audio and video. 
:guitar:
So it might be better to do a clean install. Does anyone know for sure? 
:confused:

---

### Post by zach12 on 2007-05-19
me too i Want Ubuntu Studio

---

