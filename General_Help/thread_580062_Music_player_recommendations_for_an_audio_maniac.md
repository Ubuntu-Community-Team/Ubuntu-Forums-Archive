---
title: "Music player recommendations for an audio maniac"
date: 2007-10-18
forum: General Help
---

### Post by Elotero on 2007-10-18
I just moved into my new place.. i only have 1 TV and its in mybedroom... i have a nice little loft setup with a big beanbag and a recliner chair..  i used to have some crappy Target cd player as the entertainment but i got a bright idea.. why not setup my Laptop? It plays DVDs and i have about 30, 000 mp3s/wmas.. why not setup my new loft as a Linux Lounge??? It would be an awesome way to show visitors Ubuntu.. so i set it all up, invited some folks over and took out my Linux alternative to Winamp-- XMMS... every now and again it acts up and boy was it acting up... it freakin FROZE BAD when i was uploading too many songs.. basically i was put on the spot.. here i was telling everyone i had a badass Linux Lounge setup and they dont even know what Linux is.. and im sure they think it sucks now... i am looking for a less problematic Media Player.. mostly for music.. i ended up using MPlayer which was cool but im not as in tune with it as i am Winamp/XMMS.. i tried Amarok and it crashed awhile back so i havent even been back to using it... i heard Listen is a good one and Rhythmbox was also mentioned..  i really want to quit XMMS all together... im not gonna let it embarrass me like that EVER again.. oh and i tried JaJuk too but im clueless on how to install Java... anything out there besides these that just works??

---

### Post by Denis on 2007-10-18
When I was looking for another music player, I've tried the following programs: 

[Exaile]("http://www.exaile.org/")
[Sonata]("http://sonata.berlios.de")
[Listen]("http://www.listen-project.org/")
[Banshee]("http://banshee-project.org/Main_Page")
[Quod Libet]("http://www.sacredchao.net/quodlibet/")
[Amarok]("http://amarok.kde.org/")
[Rhythmbox]("http://www.gnome.org/projects/rhythmbox/")

These are about the most popular (library based) music players. 

Personally I use Listen at the moment. But it has some minor bugs and the project looks like it's no longer active. I think it's best to try some of these players to see which one you like. 

Of course there are also xmms-based players like Beep Media Player (or BMPx) or Audacious. You may also want to take a look at [XMMS2 ]("http://wiki.xmms2.xmms.se"), which is still under development, but has a good core on which a GUI can be built (although it doesn't really "just work")

---

### Post by forestpixie on 2007-10-18
I had some problems with amarok initially crashing but since the new version it's been going constantly, I've looked at most of them but ended up back with amarok - there's also songbird - but it's abit of a bloater from all accounts

---

### Post by Elotero on 2007-10-18
> **forestpixie said:**
> I had some problems with amarok initially crashing but since the new version it's been going constantly, I've looked at most of them but ended up back with amarok - there's also songbird - but it's abit of a bloater from all accounts

Oh yea.. Songbird.. it looks REALLY nice but DAMN its bloated.. the quickest player ive sued was Mplayer but its so.. bleh.. you know... its not really great or fun to look at.. it gets the job done.. but i want a little more functionality... maybe even the ability to create a playlist...

---

### Post by LinuxNewb092 on 2007-10-18
How do I install banshee, Im new to linux?

---

### Post by p_quarles on 2007-10-18
> **Elotero said:**
> Oh yea.. Songbird.. it looks REALLY nice but DAMN its bloated.. the quickest player ive sued was Mplayer but its so.. bleh.. you know... its not really great or fun to look at.. it gets the job done.. but i want a little more functionality... maybe even the ability to create a playlist...
Songbird is still in  *very *early development, so it may not be bloated so much as not ready for use.

Amarok is absolutely my favorite music player. The current version is very stable. If you're using Gnome, however, it can be a little slow. Exaile is an Amarok clone for Gnome, and is much faster in a GTK environment, though it too is in development and not as feature-rich yet as Amarok.

I've never used it, but I know that a lot of people swear by Sonata. It's basically a front-end for the command-line Music Player Daemon (MPD), so is going to be one of the least resource-demanding options. 

Links are already in Denis's post.

---

### Post by Elotero on 2007-10-18
> **Denis said:**
> When I was looking for another music player, I've tried the following programs: 

[Exaile]("http://www.exaile.org/")
[Sonata]("http://sonata.berlios.de")
[Listen]("http://www.listen-project.org/")
[Banshee]("http://banshee-project.org/Main_Page")
[Quod Libet]("http://www.sacredchao.net/quodlibet/")
[Amarok]("http://amarok.kde.org/")
[Rhythmbox]("http://www.gnome.org/projects/rhythmbox/")

These are about the most popular (library based) music players. 

Personally I use Listen at the moment. But it has some minor bugs and the project looks like it's no longer active. I think it's best to try some of these players to see which one you like. 

Of course there are also xmms-based players like Beep Media Player (or BMPx) or Audacious. You may also want to take a look at [XMMS2 ]("http://wiki.xmms2.xmms.se"), which is still under development, but has a good core on which a GUI can be built (although it doesn't really "just work")



Youre awesome dude.. thanks for the recommendations..  so you use Listen?  Have you tried Jajuk? the think about XMMS is that it changes all the names of my files to the ID3 tags which is WEAK... i add a playlist and when it load i have no clue what the hell is palying or where to find my songs because theyre all out of order.. JaJuk has an option to view ID3 or staright up Filenames... i would rather use filenames to find my music because thats what im always fixing.. imagine.. i have been collecting mp3s since 1998 and i have so much that i take about an hour a week to fix crappy filenames.. example.. ---Rick James_-_Maryjanie ... crap like that... i fix the file name to Rick James - Maryjane... now its clean.. and freakin XMMS decides to ruin all my hardwork by converting the names back to ID3 form.. AHHHHHHHHHHHHH!!!!!!!!! Yea Jajuk is cool but it an ULTRA pain in the *** to install on Ubuntu...

---

### Post by forestpixie on 2007-10-18
yea playlists - sort of must haves really...

as I said amarok would be my choice - the only reason it gets stopped is sleep and while I've been running the gutsy tribe/rc stuff a few reboots. If you do decide to try it again I suggest you make sure you delete the hidden folder in /home before you do.

and good luck with your search for just exactly what you're looking for :D

---

### Post by forestpixie on 2007-10-18
> **LinuxNewb092 said:**
> How do I install banshee, Im new to linux?

in a terminal

```
sudo apt-get install banshee
```

---

### Post by Elotero on 2007-10-18
> **forestpixie said:**
> yea playlists - sort of must haves really...

as I said amarok would be my choice - the only reason it gets stopped is sleep and while I've been running the gutsy tribe/rc stuff a few reboots. If you do decide to try it again I suggest you make sure you delete the hidden folder in /home before you do.

and good luck with your search for just exactly what you're looking for :D

Whats up with the /home hidden folder? does it make it make it slow or something? or just makes it easier to locate my files better?  Would i just higghlight and click Delete?  Im going to try Amarok again and with heart this time.. hopefully it works nice and doesnt give me trouble in front of my company next time.. i cant tell you how embarrassing it is to close your laptop to put a cheap Target CD player on top...

---

### Post by Mode_Locrian on 2007-10-18
I'll just second all of the posts recommending Amarok--I've decided that it's not just my favorite music player for linux, it's my favorite music player, period.  I love the fact that it's essentially just an easy-to-use database with an intuitive front-end.  Highly recommended, especially if you have a lot of music...

---

### Post by forestpixie on 2007-10-18
it keeps some settings in there, so if you  had problems with any of them originally when you reinstall it uses the same folder - I had problems with updating the library at the time - everytime I put some music in my library - bam! crash! 

it's hidden in kde 
> 
/home/kevin/.kde/share/apps/amarok

just delete it before you reinstall, and I hope it plays nice this time

---

### Post by adamorjames on 2007-10-18
Banshee, it works the best out of all of them for me. It rocks. :guitar:

---

### Post by Lord Illidan on 2007-10-18
> **Mode_Locrian said:**
> I'll just second all of the posts recommending Amarok--I've decided that it's not just my favorite music player for linux, it's my favorite music player, period.  I love the fact that it's essentially just an easy-to-use database with an intuitive front-end.  Highly recommended, especially if you have a lot of music...

My sentiments exactly!

---

### Post by Denis on 2007-10-19
> **Elotero said:**
> Youre awesome dude.. thanks for the recommendations..  so you use Listen?  Have you tried Jajuk? the think about XMMS is that it changes all the names of my files to the ID3 tags which is WEAK... i add a playlist and when it load i have no clue what the hell is palying or where to find my songs because theyre all out of order.. JaJuk has an option to view ID3 or staright up Filenames... i would rather use filenames to find my music because thats what im always fixing.. imagine.. i have been collecting mp3s since 1998 and i have so much that i take about an hour a week to fix crappy filenames.. example.. ---Rick James_-_Maryjanie ... crap like that... i fix the file name to Rick James - Maryjane... now its clean.. and freakin XMMS decides to ruin all my hardwork by converting the names back to ID3 form.. AHHHHHHHHHHHHH!!!!!!!!! Yea Jajuk is cool but it an ULTRA pain in the *** to install on Ubuntu...
You're welcome

I didn't know Jajuk. It also looks good, maybe I'll give it a try later. 

The fact is that most of these library-based mucis players use the ID3 tag info to search for  track titles, artists, genres etc. I don't know exactly which of these players support searching filenames instead. 

I usually do the opposite: I don't really care about the filename, but I correct the tag of the song. The advantage of that is that your music program can easily get information about the artist, album etc. 

About amarok: I tried it. Amarok has many features, but in my opinion this makes the program rather bulky and large (the interface). Also I prefer a GTK based player, that uses the style of your Gnome environment. 

I hope you find a program that suits your needs!

---

### Post by bonejob on 2007-12-18
> **forestpixie said:**
> I had some problems with amarok initially crashing but since the new version it's been going constantly, I've looked at most of them but ended up back with amarok - there's also songbird - but it's abit of a bloater from all accounts

Bloater? I'm not so sure that is fair. It's *very* green yet (Version 0.3) - not even a beta, let alone a RC and certainly not a stable release. The program has lots of promise, but it is not yet ready to be depended on as one's primary media manager. You may or may not remember Firefox when it was at that same stage of development. It was called Phoenix back then and it was an incomplete and messy patchwork quilt with more bugs than a South Bronx tenement. It wasn't until Firebird 0.7 that I felt confident enough with it to start using it for my primary browser and it still had another whole year to go and yet another name change before it officially became a public release 1.0. The main reason people were so patient with Firefox's initial development pace was because Internet Explorer stunk so badly, Netscape was carrying tons of AOL baggage, and Opera was still adware, unless you paid them $40 to shut off the streaming ads. If IE and Netscape weren't such junk and Opera had been free, Firefox would NEVER have made it.

I think for now people should cut Songbird some slack, keep trying it every so often as new versions are released, but use some OTHER program until it is stable enough for prime time. That so many Linux users are trying it and talking about it this soon in its development cycle shows that there is really a crying need for a multimedia "killer app" for the Linux world. We have alternatives now, but for many reasons, we are looking - very hard - for something better. I think Songbird may very well be it - SOMEDAY!

---

