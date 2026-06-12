---
title: "unmet dependencies ?"
date: 2013-09-07
forum: General Help
---

### Post by Coder88 on 2013-09-07
I am wanting to install the banshee media player, but i run into issues as seen below. Any suggestions how to solve this and get banshee installed on my linux system?
(ArtistX/Ubuntu 12.10 32bit, AMD cpu).
I have already run apt-get updates and apt-get upgrade

[INDENT][COLOR=#000080][FONT=fixedsys]$ sudo apt-get install banshee
[sudo] password : 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 banshee : Depends: libgdata1.9-cil (>= 1.9.0.0) but it is not installable
           Depends: libtaglib2.0-cil (>= 2.0.4.0) but it is not installable
           Recommends: banshee-extension-soundmenu (= 2.6.1-2ubuntu1~hyper1+precise) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
$[/FONT] [/COLOR]
[/INDENT]

---

### Post by ian-weisser on 2013-09-07
Do you perhaps have some old 12.04 banshee PPA enabled?
If so, disable it.


If you are using the Ubuntu repository version of banshee for 12.10, it should be looking for version 2.1, not 1.9.
1.9 is only available in 12.04, not 12.10.
```
$ rmadison -u ubuntu libgdata1.9-cil
libgdata1.9-cil |  1.9.0.0-1 | precise/universe | all
```

---

### Post by Coder88 on 2013-09-07
> **ian-weisser said:**
> Do you perhaps have some old 12.04 banshee PPA enabled?
If so, disable it.


If you are using the Ubuntu repository version of banshee for 12.10, it should be looking for version 2.1, not 1.9.
1.9 is only available in 12.04, not 12.10.
```
$ rmadison -u ubuntu libgdata1.9-cil
libgdata1.9-cil |  1.9.0.0-1 | precise/universe | all
```

I can not find any residual banshee packages on my system. I am thinking this might have more to do with the libgdata libraries that look to be outdated, so i searched for them in Synaptic and saw they are basically for accessing online media libraries (for album art and such? buying music?), and mostly have to do with google (which i want nothing to do with anyhow!). I was going to delete the libgdata but in so doing Synaptic wanted to delete gnome, yikes! Guess I will just learn to live without Banshee. There are other media players, and I can view videos with VLC, gnome player, etc and listen to music using Songbird and other music players.

---

