---
title: "Ubuntu DVD:What is it for?"
date: 2008-05-06
forum: General Help
---

### Post by bme on 2008-05-06
I managed to get hold of a ubuntu 8.04 dvd and proceeded to install . I noticed that there is no difference between the cd and dvd in the installed ubuntu-I mean same size and apparently same contents. So what is the purpose of the dvd?

---

### Post by retrow on 2008-05-06
It can act as a repository and holds several programs that aren't installed in the default version of Ubuntu, like Blender, Inkscape, samba, emacs, etc. This DVD is useful to people who don't have access to broadband internet. If they can get hold of a DVD, then can pretty much live happily ever after - unless they are looking for some exotic programs or updates.

---

### Post by bme on 2008-05-06
I am one of those that cannot afford broadband in my country so I thought the dvd included almost everything I need. Unfortunately I still cannot play mp3 or watch movies unless I download the plugins---. Maybe if those are on the dvd then it would be worth it...?

---

### Post by sekinto on 2008-05-06
1) The DVD probably doesn't include non-free stuff, which is why you need to download things to play MP3s and watch movies... but that is just a guess.

2) Even with a bad internet connection you can still probably download vlc and libdvdcss in a fair ammount of time.

---

### Post by retrow on 2008-05-06
> **bme said:**
> Unfortunately I still cannot play mp3 or watch movies unless I download the plugins---. Maybe if those are on the dvd then it would be worth it...?Did you try searching for the appropriate packages through synaptic or Add-Remove?

Search for:
1) ubuntu-restricted-extras
2) gstreamer0.10-plugins-bad
3) gstreamer0.10-plugins-ugly
4) build-essential
5) mplayer
6) mozilla-mplayer
7) vlc

There could be some programs that can't be included on an official release because of legal restrictions, but you can add repositories and download those specific programs when you are connected to the internet.

---

### Post by bme on 2008-05-06
Thanks everyone.
I'll dl the vlc tar package and install from source....

---

### Post by bme on 2008-05-07
./configure did not work on the vlc....says "cannot create executable".....

---

### Post by christianxxx on 2008-05-07
If I'm not mistaken, you'll always need "build-essential" to build from source.
```
sudo apt-get install build-essential
```

I don't remember if kernel headers is a requirement, but search post on how to install that as well.

---

### Post by bme on 2008-05-10
Am trying LinuxMint includes almost everything I need and Ubuntu based......

---

