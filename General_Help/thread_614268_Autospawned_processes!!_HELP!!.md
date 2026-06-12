---
title: "Autospawned processes!! HELP!!"
date: 2007-11-15
forum: General Help
---

### Post by mrleinad on 2007-11-15
HELP!! I have installed mplayer and now it not only starts itself, but it forks and keeps on filling my memory and cpu resources!! What can I do?? I do killall -SIGKILL mplayer but it just keeps on starting itself, I don't know what to do! It has something to do with Ktorrent, the moment I start it begins to do this thing.

---

### Post by psypher on 2007-12-11
I have the exact same problem. Running Gutsy with gnome but use ktorrent cos I like it and as soon as I start ktorrent, mplayer process starts and runs at 100%, BLOODY ANNNOYING I TELL YOU. Brings core 2 due 2.6 to a halt!!!

Even worse is when I close ktorrent it still carries on??? Does anyone know why this happens, and why mplayer of all things??? It's not like I am even watching a preview but I have a feeling it has something to do with preview, why else would mplayer be involved in d/l torrents??

I also suggest maybe changing the title of this post to something that might get someones attention, since no-one has replied in 3 weeks!!!

eg:

Serious KTorrent problem, spawns unstopable mplayer process which causes 100% CPU usage. 

Help anyone!!!

---

### Post by matthewcraig on 2007-12-11
Have you tried to reinstall mplayer?  Or just uninstall it and use Totem?

---

### Post by psypher on 2007-12-11
I will try re-installing mplayer, but the problem is not viewing movies, as per the post the problem is when starting Ktorrent suddenly an unstoppable mplayer process starts up and the only way to stop it is to log out of gnome and back in again

---

### Post by tommcd on 2007-12-11
Perhaps removing ktorrent would help? I use gnome and transmission for torrents and mplayer runs fine. You could also use azureus. This sure sounds like a bug. File a bug report at launchpad.

---

### Post by psypher on 2007-12-11
gonna give deluge a try, i personally cannot stand azureus, had many issues with it a while ago and just got sick of it. Does it not kill your pc with it's constant resources requirement? I found that  java app  being very heavy. And the whole re-indexesing torrents for 2 hours very annoying. I read deluge is quite good. I just really like ktorrent. did everything i wanted, ah well. gonna log the fualt on launchpad as I don't find anything ike this on google.

---

### Post by psypher on 2007-12-11
bug logged:

[https://bugs.launchpad.net/ubuntu/+source/ktorrent/+bug/175494](https://bugs.launchpad.net/ubuntu/+source/ktorrent/+bug/175494)

---

### Post by matthewcraig on 2007-12-11
What is wrong with the default bittorrent client?  Not sure why everyone jumps through hoops to use buggy java bt clients, when the gnome-bittorrent works just fine...

---

### Post by psypher on 2007-12-11
The default client is too basic.
Cannot shape download traffic, you have to open a window for each download, there is no search function.

With the full apps you just open one program and everything is managed.

Just plain ease of use is what we want, thats why it's so hard to get people away from windows. You just open the default bittorent client from bittorent.com and it just works. And yes I know there a lot more issues with windows that ubuntu beats hands down. But why not let ubuntu beat windows in every aspect hands down. There is no reason it can't!

---

### Post by matthewcraig on 2007-12-11
Traffic shaping?  I just click a BT link and the file download to my computer.  Do you need trafffic shaping for Firefox's other downloads?

Search functions?  Use Google.  Why does any person need a search function in a program that is supposed to download a file?

And then you say you want ease of use.  You cannot have lots of configurable functions and also have ease of use.  Ease of use is the default client.  Complex are these Java programs that are so buggy and prone to issues.

---

### Post by mrleinad on 2007-12-11
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/ktorrent/+bug/175494](https://bugs.launchpad.net/ubuntu/+source/ktorrent/+bug/175494) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/ktorrent/+bug/175494](https://bugs.launchpad.net/ubuntu/+source/ktorrent/+bug/175494) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Thanks for all your replies to this post. Seems that the problem may be temporarily solved by uninstalling ktorrent and removing the .ktorrent folder from the users home directory (~/.kde/share/ktorrent), thus wiping all data and allowing a clean reinstall. This will also erase all of the ratio u/d for every torrent we have, but it's the only solution I've found so far. It's not definitive, because sometimes as soon as a video download is finished the problem may arise once again, but some times it does not. Definitely a bug. :mad:
With regard to using the bittorrent client, it doesn't suit my needs, primarily because if I want to download just one file and a torrent has several I'm not able to select it, it just downloads all of them, even if their size is 70 GB (which are NOT available in my HD). Also because of the traffic shaping and queueing capabilities (what if I want priorities between my torrents?)
Anyway, hope this gets fixed as soon as possible.[-o< Thanks again!! :)

P.S.: I'd love to change the title to this post, but I don't know how...

---

### Post by psypher on 2007-12-12
> **matthewcraig said:**
> Traffic shaping?  I just click a BT link and the file download to my computer.  Do you need trafffic shaping for Firefox's other downloads?

Search functions?  Use Google.  Why does any person need a search function in a program that is supposed to download a file?

And then you say you want ease of use.  You cannot have lots of configurable functions and also have ease of use.  Ease of use is the default client.  Complex are these Java programs that are so buggy and prone to issues.


well for one thing, you live in the US, where you probably have 8MB uncapped DSL with 1:3 contention or a T3 line with no shaping or restrictions for $30/mnth. I live in a country where the absolute fastest dsl connection you can get is 4MB/s and costs nearly $10 a gig whether thats upload or download, international or local, it all counts. BTW I can only afford a 384kbps line which is $40/mnth JUST FOR THE LINE RENTAL! 4MB/s is $75/mnth and it's not even true 4mb, it's just a "trial" service that some people are privvy too when they get a 1MB line.

 So just because some people live in a country where bandwidth is plentiful and the majority of your peers are actually in the same country doesn't mean that the rest of the world has that luxury. If people didn't have the need for download managers there would be no reason to develop programs like deluge, ktorrent, azureus, bittcomet, bitlord, torrentflux, etc etc. It makes life easy. Yes I can use google, but it takes twice as long to find what you want. Have you even used any of those programs?? With ktorrent you have a search box with a drop down list of all the top torrent sites. enter what you are looking for choose the site and you have a nice neat laid out page with all your results including seeds and peers to gauge what is the best download. Click on the link and voila it's already downloaded and queued with all your other torrents in a managed way, with the ability to individually stop start and shape each torrent the way you like it. Good for you that you don't need it, but there are too many people out there that do need and and love the "easy of use"

I don't quite get what you mean by you click the file and you download it. Yeah sure you can click the torrent file and download that, but once you have loaded the torrent into the torrent program you should still be able to manage the download??

Traffic shaping firefox downloads? Yes I do not use firefox for anything larger than a meg. FF d/lmanager sucks! I only use d4x. Why? so I can shape and manage my downloads and stop and resume without having to start all over again and waste more precious expensive bandwidth plus it has multithreaded downloads squeezing the most out of your connection. 

The point isn't why? There are too many reasons for, not just me but other people too, to use download managers. The questions how can we make ktorrent work the way it supposed to, relatively bug free. Instead of it wasting time, cpu cylces, electricity and giving frustrated users a slow desktop experience.

I understand that in your case the basic bittorrent prog is fine and that you don't see the point of having such a mission to get these program to work. But the point is this stuff is not supposed to be a mission, it must just work. And thats what i am trying to do, find the bugs to make the programs just work so the next guy who wants  a fully featured bittorent program that uses low resources and gets the job done efficiently and neatly can just go sudo apt-get install ktorrent and be happy.

---

### Post by puterman on 2008-01-06
I fixed this problem by temporarily renaming /usr/bin/mplayer.

EDIT:
That didn't solve the problem, and instead totem was started in the same way as mplayer.  I did some digging and discovered that the problem was with trackerd, which indexes files in specific directories, by default your home directory.  So if you download your torrents to your home directory (or any subdirectory), trackerd will keep scanning the files repeatedly while they're being downloaded, using mplayer for video files.  (Continually scanning the files in this way seems like a bug to me.)  The brute force way of fixing this is to kill trackerd.  The less brutal way would be to configure trackerd to not scan your torrent download directory.  See the man pages for trackerd, tracker.cfg, tracker-search-tool etc. for more info.

---

### Post by _Luiz_ on 2008-01-22
I found a temporary "solution" too. 

Just send the process a SIGSTOP signal. It's that simple. 

I have no idea how to do that through GUI in Gnome, but in KDE is simple:

Launch KSysGuard > Right-click on mplayer process > Send signal > SIGSTOP

Doing that lowered my HDD temperature by 9 (!) degrees. That on a laptop must be very annoying.

And it has nothing to do with tracker: I don't even use it and have the same problem.

---

### Post by Steve Kinney on 2008-02-15
Hmmm...  It's early in the game, but I just found that killing tracker does stop unwanted mplayer processes from spawning here.  

On my system (Ubuntu 7.10 plain vanilla) tracker is completely broken and useless anyway, has been for a couple of months (as far as me noticing it).  This problem persisted through a new system installation, and others have reported it as a bug.  I just used the "Sessions" editor to turn tracker all the way off - no sense wasting any system resources just letting it thrash around doing nothing useful.

Other symptoms (on my system) of tracker being broken:  Amarok loops endlessly near the end of indexing my music directory, and the Nautilus file search (ctrl-f) finds nothing or a handful of irrelevant returns.  I hammered on tracker quite a bit trying to fix it, with no improvements.  My ad hoc solution is to use the Gnome Search Tool and wait for an update or upgrade including a working version of tracker:  It worked fine in earlier versions, and I hope it will again someday soon.

A while back I had problems with KTorrent and tried literally every other client I could find.  IMO KTorrent is the best all around tool, with uTorrent under Wine a close second.  Azureus was not useable (massive resource hog as often happens with Java apps).  The "default" Gnome torrent toys are next to useless because there is no way to see or control what they are doing, and they have effectively no configuration options:  Under ideal conditions they might be "good enough" but how often are conditions ideal?

:)

---

### Post by johnnybirdman on 2008-02-16
Odd that this post started some time ago but I have not had this problem until now.  This did not happen until a few days ago.  I also noticed the cpu usage on startup (with no programs started) and discovered it was the tracker process. Something must have changed recently in the updates relating to tracker.

---

### Post by chrisccoulson on 2008-02-16
> **matthewcraig said:**
> Traffic shaping?  I just click a BT link and the file download to my computer.  Do you need trafffic shaping for Firefox's other downloads?

Search functions?  Use Google.  Why does any person need a search function in a program that is supposed to download a file?

And then you say you want ease of use.  You cannot have lots of configurable functions and also have ease of use.  Ease of use is the default client.  Complex are these Java programs that are so buggy and prone to issues.

I didn't realise ktorrent was Java based.

Gnome-bittorrent is so good that it has been replaced with Transmission in Hardy. gnome-bittorrent doesn't even have basic features such as the ability to resume downloads. If gnome-bittorrent meets most peoples requirements, then why do users flock to Transmission, Deluge, Ktorrent and Azureus? gnome-bittorrent is a joke and woefully inadequate for most people. Which is why it will be replaced in Hardy.

You have to balance ease of use with features. Transmission has it right. gnome-bittorrent sacrifices features for ease of use, which ends up making it less useful and more difficult to use (diminishing returns). The balance is very wrong. You can have plenty of features with ease of use if the UI is right.

Some people prefer more features and choose the applications that fit their needs. Why should you criticise their application choice based on your own beliefs? Is it the users fault that the application they choose doesn't work? You make it sound like that

---

### Post by johnnybirdman on 2008-02-18
> **chrisccoulson said:**
> I didn't realise ktorrent was Java based.



ktorrent is not java based.  whoever said that doesn't know what they are talking about.  KTorrent is written in C/C++ using Trolltech's Qt toolkit.

I found it to be a great program, even in gnome, until this CPU issue.

---

### Post by seijling on 2008-03-23
I found that if you disable indexing either by:

```
trackerd -n
```

or...

simply disabling it from[B][U] "System-->Preferences-->Indexing Options"
[/U][/B]
worked for me completely!


My CPU fan just dropped another level as I typed this.

Hope it helps.

Mike

---

