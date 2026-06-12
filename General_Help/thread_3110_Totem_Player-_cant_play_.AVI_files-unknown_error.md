---
title: "Totem Player- cant play .AVI files-unknown error"
date: 2004-11-03
forum: General Help
---

### Post by Borgmeister on 2004-11-03
I 'acquired' the new epsodes of Battlestar Galactica, but i am unable to run them, Totem opens, and then comes up with 'unable to play file, unknown error'. Im thinking its codecs, and if it is, where do i get them? If its not, any ideas?

---

### Post by im_ka on 2004-11-03
codecs are tricky.

try mplayer, it plays (almost, if not) every known video format.

edit your sources list by
```
sudo gedit /etc/apt/sources.list
```
add this line:
```
deb ftp://ftp.nerim.net/debian-marillat/ unstable main
```

run
```
apt-get update
```
and you'll be able to install mplayer via synaptic

---

### Post by jdusablon on 2004-11-03
If it's DivX or XVid, this should get totem to play 'em.

1. Make sure Universe repository is added to sources.list. To do this, see [here](http://www.ubuntuforums.org/showthread.php?t=179).
2. Open Synaptic (or use apt-get,) select and install totem-xine

---

### Post by zevoneer on 2004-11-03
There is a whole set of instructions for multimedia in the How To section that will walk you through everything you need to install MPlayer and all the libraries you'll need to get commercial DVD'S to run. Be prepared to do lots of typing in the terminal but it is an excellent guide. Even if you install Xine you won't be able to play commercial DVD's without libdvdcss to decode them.

---

### Post by jdusablon on 2004-11-03
That's true, of course, but Borgmeister had simply asked about 'aquired' video. I assumed that this meant compressed MPEG4 or whatever and that they wanted a quick way to get them playing. (the title mentions AVI)

---

### Post by zevoneer on 2004-11-03
Noticed the AVI after I'd posted but I highly recommend the How To anyway for DVD playing. It also has a section on MP3's. It's well worth taking the time to work through it.

---

### Post by Borgmeister on 2004-11-03
Well, when i say aquired, i  mean, i used suprnova, and azureus, on my windows booxen, as a huge fan of the original, i knew i must see these episodes. However, a friend of mine, whom is my manager also, got shafted, and thus couldnt get home to see it. I was going to let him use my laptop at lunchtime to view it. But totem wasnt working, so i burned it to disk. Thanks for the tips guys, you have been really helpful.

Good evening

Borgmeister

PS. I use linux exclusively on my laptop, kinda to firce me to use linux, cos sometimes, i look at windows, and think, wow that just works. I am getting there slowly, and i love the command line, feels like im back in 1994, trying to get doom to run hehe.

All the movies run great now btw. But, i dont get sound within games. Sorry, any ideas?

---

### Post by jdusablon on 2004-11-03
I agree about setting up DVD playage with MPlayer, I don't care too much for Totem anyhow. It's flaky at times. When I right-click the video-part of a playing AVI, totem crashes. hmph.

---

### Post by Borgmeister on 2004-11-06
Ok, i was clutching at straws, i didnt knw what to do, i was getting no sound in any of the games i had downloaded from the repository, so i thought what the frack, why not see if hoary offers the solution! well, he didnt, infact he made things worse, now, i can play my videos, but i cannot get sound with them. Again, i ask for your help. 

Thanks again

Borgmeister

---

### Post by im_ka on 2004-11-06
mplayer rulz! not only because it's hungarian :)

---

### Post by andy_sp1ke on 2004-11-06
Totem-Xine definitly works, which is a start. I am dealing with the same media player issues. Now have XMMS for MP3 and Totem-Xine for movies. Working on MPlayer but having a few problems with it, I have a thread about it if people know much about getting MPlayer to work!!

Andy

---

### Post by Borgmeister on 2004-11-07
Ok, hoary is all good now, it was just a case of apt-get install w32codecs. totem now plays tham fine. But i still get no sound in my games, i really need some help here!

---

