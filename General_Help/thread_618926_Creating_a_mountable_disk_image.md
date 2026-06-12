---
title: "Creating a mountable disk image"
date: 2007-11-20
forum: General Help
---

### Post by Tyke91 on 2007-11-20
I'd like to create a mountable disk image of starcraft brood war so that my friend and I can play on a LAN network together (as of right now, we can only play SC Original, which, while good... is no where near as good as BW) I've got 2 computers, one Ubuntu and one Windows, and there is a working LAN connection between them.

what I want to do is to install it on both machines, then mount the image on my machine and run it from that, and give the disk to him so he can run it on the windows machine in the other room. 

is there an easy way I can do this?

---

### Post by mouseboyx on 2007-11-20
Possibly K3B will do the job.
```

[COLOR=Red] sudo apt-get install k3b[/COLOR]
```Or if you are good with the command prompt, or dont mind it use this howto

 [SIZE=3][COLOR=Red][http://linuxreviews.org/howtos/cdrecording/](http://linuxreviews.org/howtos/cdrecording/)[/COLOR][/SIZE]

---

### Post by Tyke91 on 2007-11-21
hmm... I don't want to create a CD, I just want the image of the cd that I can mount when I need to...

I'll keep searching.

---

### Post by mouseboyx on 2007-11-21
you have to create the image first.
are you asking where to download an illegal image?

to [COLOR=Red]mount[/COLOR]:
[http://www.techspot.com/vb/topic483.html](http://www.techspot.com/vb/topic483.html)

---

### Post by Tyke91 on 2007-11-21
lol! no, I don't want an illegal image. I want to create an image so that I can mount it on my computer and play a LAN game with my friend. I bought 2 CDs, but one is now in 2 pieces and I don't want to go buy a copy of a game I already paid 2x for.

I now know how to mount it, but how would I create such an image?

---

### Post by mouseboyx on 2007-11-21
You can search before posting i learned this the hard way... So many questions that are already answered. Or search on google syntax:
```
problem+ubuntu
```
LOL

[SIZE=5][COLOR=Red]http://ubuntuforums.org/showthread.php?t=6509[/COLOR][/SIZE]

---

### Post by erginemr on 2007-11-21
> **Tyke91 said:**
> lol! no, I don't want an illegal image. I want to create an image so that I can mount it on my computer and play a LAN game with my friend.

I now know how to mount it, but how would I create such an image?

Hello,

The following address both describes how to create and mount images under Linux:

[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+CD-IMAGES](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+CD-IMAGES)

And the following one shows how to mount images only:

[http://www.cyberciti.biz/tips/how-to-mount-iso-image-under-linux.html](http://www.cyberciti.biz/tips/how-to-mount-iso-image-under-linux.html)

You can also use the Gnome CD burning program Gnome-Baker, which allows you to copy existing CD's on to ISO images. You can install and try Gnome-Baker with:

sudo aptitude install gnomebaker

---

