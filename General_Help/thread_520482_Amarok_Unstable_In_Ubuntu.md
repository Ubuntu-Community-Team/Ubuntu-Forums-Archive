---
title: "Amarok Unstable In Ubuntu"
date: 2007-08-08
forum: General Help
---

### Post by arbulus on 2007-08-08
I've been trying to run Amarok in Ubuntu Feisty for some time now with very little luck.  Amarok is very very slow on launch, sometimes taking up to a minute to a minute and a half to load.  When I frist started trying to load my library, it would crash halfway through.  It took 3 tries and crashes before it ever loaded my library.  After that, it would just randomly freeze up and crash.  Trying to do more than one thing at a time will cause it to crash (i.e. looking through menus while a song is playing).  And the crashing is not just a matter of relaunching the app, it freezes my entire system so that I have to reboot my machine.  I also get frequent errors from "knotify" and it gives me the option of ignoring it or installing aRTs (which crashes Amarok if I try to install).  If I ignore it, it will just go away and be fine for a while, but will freeze up totally soon after.

Is anyone else familliar with this problem?  Does anyone have any advice on how to correct this?

My specs:
I have a Dell Dimension E520 AMD Athalon 64bit Dual Core Processor 1.9Ghz, 1GB ram, nVidia Geforce (can't remember which number) graphics card, Ubuntu Feisty, Compiz Fusion.

Thanks in advance for your help!

---

### Post by forestpixie on 2007-08-08
I did have some issues with Amarok - every time it updated my library it would crash - never froze me out completely though. I've had the aRTs problem - but ignoring it worked for me.

I assume that you have the current version - I uninstalled and also before I reinstalled I made sure that I deleted the hidden Amarok folder - I haven't had a problem since.

Have you looked at the AMarok forum or reported the problem?

---

### Post by gavin72 on 2007-08-08
You should give **exaile** a try.

[http://www.exaile.org](http://www.exaile.org)

The best thing I like about it, is that it can display your own cover art (not mis-matched amazon searches) On Your Desktop at any size or position you want.

It's also got smart and dynamic playlists etc etc.

To get the latest version : (From the website)

Ubuntu Repository

Users of Ubuntu Feisty can optionally use this repository. Add this line to your /etc/apt/sources.list
```

deb http://download.tuxfamily.org/syzygy42 feisty exaile
```

and then type the following:
```

wget http://download.tuxfamily.org/syzygy42/8434D43A.gpg
sudo apt-key add 8434D43A.gpg
sudo apt-get update
sudo apt-get install exaile
```

---

### Post by happysmileman on 2007-08-08
Well Amarok is a KDE program and uses many KDE-specific features, it goes slow on GNOME and can have many problems

---

### Post by forestpixie on 2007-08-08
wouldn't say it goes slow - it just takes a little bit longer to load, but I'd agree it can have problems

---

### Post by DJMatty on 2007-08-08
I've had problems with Amarok under Gnome too... kNotify errors, crashes, and once when I had set it up to use MySQL to store its data every time I exited Amarok it prompty forgot all my collection. So when it started up again it went through and re-read my collection, and then wouldn't add it again.

I uninstalled it and am now happily using Exaile.

Matt

---

### Post by arbulus on 2007-08-08
Thanks for all the great input.

I looked around the Amarok website and saw a faq that said it needs KDElib and QT to run correctly.  That could be part of the problem.  I don't really have any experience running KDE apps under Gnome, but I've heard anecdotally that the QT libraries tend to slow down a system a bit.  Does anyone know if this is actually the case?

I also had a look at the Exaile website and that looks really promising.  I saw though that it's only ver 0.2.  For anyone who has used it: Is it fairly stable and easy to use?

---

### Post by constrictor on 2007-08-08
I use it now and it's worked Flawlessly for me. Once in a while (a very very long while) I get the aRTs output issue as well but i just ignore it and it's as though nothing happened at all.

---

### Post by dmizer on 2007-08-08
i had loads of problems with amarok, and i finally popped on the amarok irc room and a very helpful soul gave me the answer.

amarok does not work with ubuntu's open java alternative.  you need to use sun java instead.

download and install sun java (you can find it on sun's website).
then you'll have to set sun java to run when opening by doing the following:
```
sudo update-alternatives --config java
```
and select the sun jdk

this makes amarok work flawlessly.

---

### Post by arbulus on 2007-08-08
Apparently, the kdelibs were already installed, so I tried dmizer's suggestion for the Java, and it seems like that may have done the trick.  Amarok launched faster than it ever has and worked well while using it.  So I'm going to tentatively say that this problem is solved.

I'm also going to give Exaile a shot and see how it goes as well.

Thanks everyone for your help!

---

### Post by netimen on 2007-08-16
I have also done trick with java, but amarok still works VERY slow

---

### Post by zeta on 2007-08-17
Amarok can be very slow with large music collections. I read somewhere the threshold is around 20 Gigs. The reason seems to be the built-in database. I recommend using MySQL, it certainly worked for me (I got about 40 Gigs of mp3s).
One word about Exaile: Although it looks very promising - a potential Amarok-killer at least for Gnome-desktops - I don't think it is ready yet. On my system Exaile didn't recognise the covers of about 40% of my music and it crashes sometimes. :-s

---

### Post by netimen on 2007-08-17
Thank you, I'll switch to MySQL as soon as possible. But how slow database affects playlist sorting??

---

### Post by Songwind on 2007-08-17
As far as performance goes, I have had some very good luck with Songbird.  It is still a young project, but it performs well.  It loaded my (large, network-hosted) song library a lot faster than Amarok or Rhythmbox.

---

### Post by j2fraser on 2007-08-17
You may also want to check out [Banshee]("http://www.banshee-project.org/Main_Page"), which I prefer to Exaile. I can't speak to the relative technical merits of each though...

---

### Post by netimen on 2007-08-17
I have switched to MySQL but Amarok still works PAINFULLY slow - rating assignment to 7000 songs takes more than a minute

---

