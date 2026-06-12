---
title: "A bunch of problems"
date: 2008-04-28
forum: General Help
---

### Post by ashaiba on 2008-04-28
1. I can't seem to be able to play DVD's, i completly forgot how to make it so it allows DVDs.

2. I heard about a virtual machine on ubuntu, and do you that if i installed XP, i can insert my VAIO Disk in there to put all my drivers on that virtual machine, or will it tell me that its not a Sony VAIO Computer.

3. whenever i try to Dual Screen on NVidia X Server Settings and i click Save to Config File i get a message saying "Unable to create new X config backup file '/etc/X11/xorg.conf.backup'."

4. How do i backup DVD's like DVDShrink on Windows XP effectivly, K9Copy will closes and stops working whenever i try to backup.

5. Any great themes you guys recomend, im getting kind of tired of my current theme, maybe there is something new and exciting that i can put on, i cant seem to find anything to great on gnomelook, but thats just me, well see what you have

6. On my FIREFOX browser, whenever i watch youtube videos, the videos are very laggy, and in order for a streaming or flash video or object to work, i have to click this dumb giant PLAY button. I never had this on Ubuntu 7.10, only on Ubuntu 8.04, any way to get my streaming flash vids back to normal?

---

### Post by stoneage on 2008-04-28
For playing DVDs you could look here -
[https://help.ubuntu.com/7.10/musicvideophotos/C/video.html](https://help.ubuntu.com/7.10/musicvideophotos/C/video.html)
It is for 7.10, but for Hardy it is probably similar

---

### Post by ghost_ryder35 on 2008-04-29
> **ashaiba said:**
> 1. I can't seem to be able to play DVD's, i completly forgot how to make it so it allows DVDs.

2. I heard about a virtual machine on ubuntu, and do you that if i installed XP, i can insert my VAIO Disk in there to put all my drivers on that virtual machine, or will it tell me that its not a Sony VAIO Computer.

3. whenever i try to Dual Screen on NVidia X Server Settings and i click Save to Config File i get a message saying "Unable to create new X config backup file '/etc/X11/xorg.conf.backup'."

4. How do i backup DVD's like DVDShrink on Windows XP effectivly, K9Copy will closes and stops working whenever i try to backup.

5. Any great themes you guys recomend, im getting kind of tired of my current theme, maybe there is something new and exciting that i can put on, i cant seem to find anything to great on gnomelook, but thats just me, well see what you have

6. On my FIREFOX browser, whenever i watch youtube videos, the videos are very laggy, and in order for a streaming or flash video or object to work, i have to click this dumb giant PLAY button. I never had this on Ubuntu 7.10, only on Ubuntu 8.04, any way to get my streaming flash vids back to normal?


1. download all the gstreamer plugins (make sure to have third party repos enabled for this, might be able to do...)
```

sudo apt-get install gstreamer*

```2.it will tell you its not a sony vaio, check out virtual box or vmware for virtualization, also check out the virtualization forum here
3.you might be getting denied because of permissions.  make sure to open the file from the terminal with 
```

sudo gedit whatever the file location is that you want to edit

```4.i use dvd9to5 and k9 copy (havent had that close on me)
5.i like glossy blue
6.grrr.  I havent seen this in Ubuntu, only saw it in Fedora.  I'll google it some and let you know what I find.

---

