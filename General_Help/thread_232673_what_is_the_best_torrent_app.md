---
title: "what is the best torrent app?"
date: 2006-08-09
forum: General Help
---

### Post by Nemesis Teufel on 2006-08-09
I dont know if this is the place to post. Sorry if I been wrong.


azareus? bittornado? or which?
My speed cnx is 1mb.

---

### Post by em3raldxiii on 2006-08-09
I've always used Azureus.

Interestingly the newest Opera browser supports bittorent ... haven't used it much myself yet.

---

### Post by PacShady on 2006-08-16
I've used a few bittorrent apps in both Windows and Linux, and I've stuck with Azureus. It doesn't retrieve so much useless data like some of the others do, it gives you loads of information about the torrent your downloading, and it connects to a distributed database which lets you connect to other users even if the tracker of a particular torrent is down. [Download it here!]("http://azureus.sourceforge.net/")

'Shady

---

### Post by disciple on 2006-08-16
> **PacShady said:**
> I've used a few bittorrent apps in both Windows and Linux, and I've stuck with Azureus. It doesn't retrieve so much useless data like some of the others do, it gives you loads of information about the torrent your downloading, and it connects to a distributed database which lets you connect to other users even if the tracker of a particular torrent is down. [Download it here!]("http://azureus.sourceforge.net/")

'Shady
i've recenty come back to azureus

oddly enough, i don't like the gui clients on linux ( on win, had utorrent, and bitcomet)
on linux, i've uses torrentflux , bittornado, ktorrent, rtorrent, and qtorrent.. 

none of them really grabbed me, though i used bittornado as my client, till i remembered azureus.. lol

i love it, but on my machine, performance takes a hit due to java ( hopefully, with java 1.6, it'll speed up)

hmm. now seeing somethng about g3torrent ( python)
[http://www.ubuntuforums.org/showthread.php?t=18369](http://www.ubuntuforums.org/showthread.php?t=18369)

---

### Post by vycman on 2006-08-18
HI! I'd like to use a Torrent Client, uses UDP protocoll, not TCP. Please somebody tell me which torrent client supports udp. I need it, because my internet supplyer don't counts the data with UDP, and I have a limit (30GB).:)

---

### Post by KrakensDen on 2006-08-20
utorrent. It's a windows application, but it works beautifully in WINE ;).

---

### Post by stoeptegel on 2006-08-21
Did someone say KTorrent already? :mrgreen:

---

### Post by sabredog on 2006-08-21
I never got UPNP to work running utorrent under Wine.

Using Azureus and trying to ignore the Java slowdown.

---

### Post by armandg on 2006-08-21
> **KrakensDen said:**
> utorrent. It's a windows application, but it works beautifully in WINE ;).

I'm using uTorrent through wine aswell. I've never liked Azureus since it uses WAY too much memory.

---

### Post by AnthoMacP on 2007-04-22
My general experience with torrent clients on ubuntu are as follows:
KTorrent - works very well, torrents tend to go quickly but it launches KNotify and HTTP browsing every so often and it sometimes causes my ubuntu to freeze, probably because it was designed for KDE and not gnome.
Azureus - bit of a system hog but also works well.
rTorrent - no gui front end, if that doesn't bother you this is great for low resource, decent transfers
QTorrent - very simple python torrent client, lacks a lot of information and torrents tend to be slower, there also seems to be quite a few hash errors at least for me when I use it.
Torrentflux - my least favorite, runs out of your browser, but you have much better options, i would never go with this unless I had to.

---

### Post by Ekstreme on 2007-04-23
Deluge is OK. Still in development, but it's simple and looks good. Transfer rates are not the greatest. I personally stick to uTorrent with Wine, but would like to only use a native app like deluge, when it's a bit more mature

---

### Post by nphx on 2007-04-25
I was using Deluge, Azuerus, Frostwire, etc... But wow nothing compared to Transmission. It's a new very over due torrent client. Very fast, and the program runs very discreet on the resources in a GTK environment. The functionality is awesome! Guys get this. It's better than utorrent.

[http://transmission.m0k.org/](http://transmission.m0k.org/)

dowload the deb packages:

**Feisty Fawn:**
[http://ubuntuforums.org/attachment.p...8&d=1177478254](http://ubuntuforums.org/attachment.p...8&d=1177478254)

**Edgy Eft:**
[http://transmission.m0k.org/forum/viewtopic.php?t=1506](http://transmission.m0k.org/forum/viewtopic.php?t=1506)

---

### Post by trippinnik on 2007-04-25
Yeah just thought I would way in on this.  Azureus uses way too much resources, I've also used uTorrent in wine, but it lacked UDP, the speed seemed limited because of win98 network stuff (i think), I was using Ktorrent until it recently started crashing all the time, but it was fast lightweight and did the UDP deal well.  I found deluges dl speed pretty slow, and now I am back with transmission... I'm getting around 900KB/s about now.  So that's what I would recommend.

---

### Post by stokedfish on 2007-04-25
RTorrent!

---

### Post by zvacet on 2007-04-25
I don´ know how many torrents I tryed and decide to use utorrent with wine.But today I tryed **Transmission** and that´s it.best I ever tryed.Very basic and ascetic but doing job perfect.If you want to try put  this lines in your source list
```
## Transmission
deb http://acorbeaux.free.fr/ubuntu feisty main
```

save and close

```
sudo aptitude update
```
```
sudo aptitude install transmission
```

---

### Post by Cenotaph on 2007-04-26
Hmm. I've got used to use uTorrent as a windows user, and it's a great application, many functionalities, easy to use and very lite. So, that's what i use in ubuntu as well, i recommend it, it works great with wine.

---

### Post by Aberrix on 2007-04-26
rtorrent

---

### Post by Chriš on 2007-04-26
The problem with Transmission is that it currently does not support selective file downloading. For example, with uTorrent you can select which files you want to download within a torrent, so you don't have to download the whole thing.

That is my biggest gripe with it.

---

### Post by justin whitaker on 2007-04-26
> **nphx said:**
> I was using Deluge, Azuerus, Frostwire, etc... But wow nothing compared to Transmission. It's a new very over due torrent client. Very fast, and the program runs very discreet on the resources in a GTK environment. The functionality is awesome! Guys get this. It's better than utorrent.

[http://transmission.m0k.org/](http://transmission.m0k.org/)

dowload the deb packages:

**Feisty Fawn:**
[http://ubuntuforums.org/attachment.p...8&d=1177478254](http://ubuntuforums.org/attachment.p...8&d=1177478254)

**Edgy Eft:**
[http://transmission.m0k.org/forum/viewtopic.php?t=1506](http://transmission.m0k.org/forum/viewtopic.php?t=1506)

Let's see, the first link is blocked by websense, the second goes nowhere, and the third is for edgy. Guess I can compile it.

Right now, I'm using BitTorrent and Bittornado. Better speeds then Deluge, and so long as I'm not downloading 5 files at once, it's fine.

I do miss uTorrent though. That's one application that is a best of breed.

---

### Post by Chriš on 2007-04-26
> **justin whitaker said:**
> Let's see, the first link is blocked by websense, the second goes nowhere, and the third is for edgy. Guess I can compile it.

Right now, I'm using BitTorrent and Bittornado. Better speeds then Deluge, and so long as I'm not downloading 5 files at once, it's fine.

I do miss uTorrent though. That's one application that is a best of breed.

Is it available in this repository that was listed above?

```

deb http://acorbeaux.free.fr/ubuntu feisty main

```

---

### Post by unnes on 2007-04-26
Transmission is pretty and stable, but it doesn't support DHT. Azureus has the full featureset but, as everyone knows, is a memory hog.

I tried Deluge recently and while it supports most of the desirable features on paper, it doesn't run that well.

My personal pick: qBittorrent. It doesn't support encryption (yet), but is the closest thing I could find to uTorrent on Windows (which is just too much of a hassle to run through WINE).

[http://www.qbittorrent.org/](http://www.qbittorrent.org/)

---

### Post by ghandi69_ on 2007-04-26
Maybe its just me, but I found Ktorrent to be the most similar to uTorrent from windows, which is a highly regarded torrent program.

I use Ktorrent.

---

### Post by unnes on 2007-04-26
> **ghandi69_ said:**
> Maybe its just me, but I found Ktorrent to be the most similar to uTorrent from windows, which is a highly regarded torrent program.

I use Ktorrent.

Ktorrent doesn't play well with GNOME :(

---

### Post by hotani on 2007-04-26
anything with functional rss feeds. So Azureus in other words.

I prefer ktorrent, but I have az set up to automatically download all my TV shows and it is always running. Until I find another one that will do that, I'll have to stick with it.

---

### Post by ghandi69_ on 2007-04-26
> **unnes said:**
> Ktorrent doesn't play well with GNOME :(

I have been using Ktorrent in gnome for quite some time without any issues.. maybe I'm just lucky.

---

### Post by jonom on 2007-04-26
ktorrent is working great under gnome for me too.

---

### Post by kelvin spratt on 2007-04-26
i've used the lot deluge is not in the game utorrent was good but now sold out to bittorrent who sold out to mpaa
so they are out so its the blue frog and ktorrent and on linux ktorrent with gnome maxes out for me its all in the settings as with the blue frog get them right a awesome application think you know best a waste of time trying 
to use them but if i went back to windows i think ktorrent would come to

---

### Post by robenroute on 2007-04-29
> **kelvin spratt said:**
> i've used the lot deluge is not in the game utorrent was good but now sold out to bittorrent who sold out to mpaa
so they are out so its the blue frog and ktorrent and on linux ktorrent with gnome maxes out for me its all in the settings as with the blue frog get them right a awesome application think you know best a waste of time trying 
to use them but if i went back to windows i think ktorrent would come to

Where can I download the English subtitles for this post?

Thanks   :lolflag:

---

### Post by jugs on 2007-04-29
Been asked a thousand times, and I'll answer it a thousand and one.

rtorrent

---

### Post by Nythain on 2007-04-29
i've always prefered ktorrent... had everything i wanted and needed, till it started crashing after running for a couple hours... we cant have that in the wondefull world of torrents.

Im currently trying qbittorrent, though it doesnt offer me near the options and functionality of ktorrent.
Azureus wouldnt give me the speeds i wanted, and was waaaaaay to resource consuming.
guess im gonna check out this rtorrent others are talking about and see how it compares to ktrorrent and qbittorrent

---

### Post by unnes on 2007-04-30
> **Nythain said:**
> i've always prefered ktorrent... had everything i wanted and needed, till it started crashing after running for a couple hours.

The crashing problem on Feisty is related to DHT. So either disable DHT in your version of ktorrent or upgrade to the latest build (2.1.4) from ktorrent.org. Hopefully it will work again!

---

### Post by Flump5000 on 2007-05-23
does anyone know if they make utorrent for ubuntu?  i always liked that on windows and transmission on my mac.

---

### Post by DjBeck on 2007-05-23
> **Flump5000 said:**
> does anyone know if they make utorrent for ubuntu?  i always liked that on windows and transmission on my mac.
Unfortunately not ... you can get it up and running through wine though.

I really like rtorrent, it's light weight and very easy to use.

---

### Post by 320kbps on 2007-06-02
utorrent is the best. hands down.

---

### Post by jjacobs2 on 2007-06-02
Deluge seems to work well for me.  It has enough options without being bloated or having lots of dependencies.  Utorrent is decent although any modern computer can run pretty much any torrent client and feature wise utorrent is about average.

---

### Post by paark.s on 2007-10-12
rTorrent is still my choice. But I am trying Azureus.

---

### Post by em3raldxiii on 2007-10-14
Last time I put in my vote, I think I suggested Azureus.  However, over time I have become very fond of kTorrent!  I know I know ... it's a KDE native app and I am running Gnome.  Still, it's a fabulous torrent handler.  I recommend everyone gives it a try.

---

### Post by r-mo on 2007-10-14
I use uTorrent under wine and occasionally transmission if i'm on a ssh.  Would use deluge but the scheduler is a killer feature for me.

---

### Post by deadlikeoscar on 2007-10-14
Deluge has a scheduler unless I am not understanding you correctly. It is a plugin.

---

### Post by r-mo on 2007-10-14
> **deadlikeoscar said:**
> Deluge has a scheduler unless I am not understanding you correctly. It is a plugin.

Great :) I didn't know that.  uTorrent works great in wine but I'd far rather be using a native gtk app :)

---

### Post by wkdown on 2007-10-14
I dont know about anyone else, but I am seeing some uploading issues with KTorrent.  I primarily use Demonoid for my torrents.  Its membership is restricted for many reasons.  One thing they do is if you are not sharing enough, basically never seeding, they boot you.  Well lately, alot of torrents I DL fine but I almost never upload.  I can see that there are plenty of leechers and not alot of seeders, but my swarm is almost always empty.  I have my cap at 0, so its never throttled by me, and I even manually reannounce the tracker.  So my concern is if KTorrent is notorious for this and, if so, what is a good app to move to?  I refuse to use Windows emulators so uTorrent is out, and I've heard too many bad things about Azerus' JAva interface.  I prefer a GUI because it makes torrents alot easier to manage.  Any ideas?

---

### Post by Leetbumble on 2007-10-18
Anyone know of a client that can use HTTPS, some other students on my university's network have p2p clients running on HTTPS and its one of the only prots that can get around the packet shapper / firewall my school IT has.

Thanks so much

---Gutsy and loving every minute of it.--

---

### Post by arethz on 2007-11-04
I choose Deluge for my torrent client because it has a simple look and easy to use.:popcorn:

---

### Post by airtonix on 2007-11-09
+1 rTorrent

There is this GUI frontend for rtorrent. [http://code.google.com/p/ntorrent/](http://code.google.com/p/ntorrent/)

Try this, run rTorrent on a remote box(in a spare room, so no-one is annoyed by the machine.)
 and have it setup to : 
 - only download X amount of torrents at a time.
 - move finished torrent to a 'finihsed' folder.
 - watch a 'torrent-queue' folder for torrents and : 
   + start new torrents
   + stop removed torrents
 
then setup have rtorstats run every 10minutes, making it output a webpage.

share the torrent-queue folder over your local-network.

on your normal workstation(aka normal computer, aka not the server) copy any torrent files you find into this shared torrent-queue folder

rtorrent will automatically start them.

when you remove the torrent, rtorrent will stop them, but not remove it from the queue.(this is a option to have setup in conf files)

so also you need to make a torrent-pending folder where you will put torrents on hold.(youll kick yourself if you have to search for that torrent file again.)


I test azerus on a celeron 333mhz 256ram setup, it takes a very long time to hash check each torrent.

where as rtorrent on the same system, in the same time  amount of time it takes to hash check one torrent, its already done the lot!

plus, i can actually use the system for other things other than timesharing the mouse cursor with azerus.

---

### Post by Kymus on 2007-11-09
I tried using Azureus on Windoze and my torrents never went anywhere, so I switched to uTorrent and loved it. Now that I'm on ubuntu, I switched to KTorrent since it was suggested that it is the linux variation of uTorrent. I'm largely pleased with KTorrent; I like the speed bars on the icon in the system tray, I have found the GUI to be much more pleasing than that of uTorrent (which I did like), and I have never had any issues with it crashing in my gnome environment. The only gripe I have is that I preferred uTorrent's preferences menu :P.

---

### Post by Promaster91 on 2007-11-22
I use utorrent and I don't have any problems. You will have to use wine to run it but is doesn't take up much memory as bittorrent and has more useful features.

---

### Post by Cannaregio on 2007-11-22
Was using Azureus.
Switched to deluge and I'm very happy with it: simple, very quick, cut all mustards.

Just my 0.02 euro.

---

