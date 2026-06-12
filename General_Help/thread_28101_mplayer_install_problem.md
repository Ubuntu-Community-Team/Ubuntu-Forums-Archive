---
title: "mplayer install problem"
date: 2005-04-18
forum: General Help
---

### Post by lee_connell on 2005-04-18
im trying to install mplayer and im getting a bunch of dependency errors, saying it's missing libc6 greater than what's installed and various other files.  Am I setting up the wrong repo or something. Help please!

Lee

---

### Post by bored2k on 2005-04-18
You'd have to say what repos you are using for us to know if they're wrong don't you think ?


Fix:
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)
[http://ubuntuguide.org/#mplayer](http://ubuntuguide.org/#mplayer)

---

### Post by makis on 2005-04-19
Hi,

I have the same problem with different libraries. Have a look here:

[http://ubuntuforums.org/showthread.php?t=26824](http://ubuntuforums.org/showthread.php?t=26824)

nobody could help me!! 

Did u solve your problem?? How??

thx

Makis

---

### Post by laka on 2005-04-19
[QUOTE=makis]Hi,

I have the same problem with different libraries. Have a look here:

[http://ubuntuforums.org/showthread.php?t=26824](http://ubuntuforums.org/showthread.php?t=26824)

nobody could help me!! 

Did u solve your problem?? How??

thx

Makis[/QUOTE]

As bored2k said, just look at the mplayer-install section on the [http://ubuntuguide.org](http://ubuntuguide.org)

---

### Post by lee_connell on 2005-04-19
yeah repos would help eh?

[ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) unstable.

I'll look at the guide thanks

---

### Post by sb73542 on 2005-04-19
[QUOTE=lee_connell]yeah repos would help eh?

[ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) unstable.

I'll look at the guide thanks[/QUOTE]

The guide says NOT to use marillat.  There are a million mplayer packages in Ubuntu's repos, not sure which, but their dependencies are not available.  That is what the problem is.  The guide is wrong.

---

### Post by darkaudit on 2005-04-20
I've found that the best way to get a working mplayer is to build one's own .deb. This is recommended by the mplayer developers themselves. The source package includes instructions on how to build the .deb.

I also used some suggestions from this page:

[http://www.princessleia.com/MPlayer.html](http://www.princessleia.com/MPlayer.html)

especially the suggested packages to install. One needs the dev versions on the codec packages to install support in mplayer. This includes nvidia-glx-dev if you have an nvidia card.

One caveat, though. Not all the switches used in this example actually work. I suggest --disable-runtime-cpudetection --enable-gui and --enablemenu.

---

