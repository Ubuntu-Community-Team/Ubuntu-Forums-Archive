---
title: "What media player?"
date: 2006-09-06
forum: General Help
---

### Post by rekahsoft on 2006-09-06
I have been using Banshee 0.11.0-cvs and prior versions and have found that it takes forever to load my music library which is very large (44gb and growing :))...the GUI freezes up and takes time to load (quite a bit of time)...is there a media player that is good and can handle a very large library quick and efficiantly...it has to have support for podcasts and it would be nice if there were some other cool features too. Thanks.

---

### Post by chippy99 on 2006-09-06
Try Amarok, I like it :p

---

### Post by Dinerty on 2006-09-06
I use Gxine movie player, very nice little program, very quick and stable

---

### Post by orb9220 on 2006-09-06
Amarok 1.4.3 now

echo "deb [http://kubuntu.org/packages/amarok-latest](http://kubuntu.org/packages/amarok-latest) dapper main" >> /etc/apt/sources.list

apt-get update

apt-get install amarok amarok-engines

---

### Post by rekahsoft on 2006-09-06
I i also should have noted i don't want any KDE program...only apps that use the gtk...i also would like the app to use gstreamer...btw...i have tried amarok but i am not a big fan..i like banshee except for the fact that it takes forever to load my music library...Thanks for you opinions :)

---

### Post by rekahsoft on 2006-09-06
Also note...i would like it to be able to play video podcasts and such...it would also be nice if it could sync ipods and other mp3 devices...i don't know if this is a little over the top but all i can do is ask :)

---

### Post by Dinerty on 2006-09-07
> **orb9220 said:**
> Amarok 1.4.3 now

echo "deb [http://kubuntu.org/packages/amarok-latest](http://kubuntu.org/packages/amarok-latest) dapper main" >> /etc/apt/sources.list

apt-get update

apt-get install amarok amarok-engines

Thanks for advertising this, just installed it now :)

---

### Post by puppy on 2006-09-07
I find Amarok to be good - while it takes a little time to create the initial "collection" when you first install the program (I have about 25GB of music files and it took about 3-4 minutes I think) once that's completed it's like lightning every time I access the program - Amarok creates a little sql database to store all the file data - obviously an efficient way to handle it all... :mrgreen:

---

### Post by Hairy_Palms on 2006-09-07
try listen music player its my fave by far, [http://listengnome.free.fr/](http://listengnome.free.fr/)

---

### Post by Dinerty on 2006-09-07
> **Hairy_Palms said:**
> try listen music player its my fave by far, [http://listengnome.free.fr/](http://listengnome.free.fr/)

Just installed this, quite nice indeed, rekahsoft I recommend this, does podcasts to :)

---

### Post by rekahsoft on 2006-09-07
Holy crap...this is by far the best music player for linux at the moment (in my opinion)...i wish i could migrate my podcasts over from banshee tho...

---

### Post by rekahsoft on 2006-09-08
ok..i am having a problem downloading podcasts...it says it is downloading but the progress bar doe not budge for a very ling time.

---

### Post by amgeex on 2006-09-08
What's so wrong with RhythmBox? I use it and it's great. It uses gstreamer btw. :D

---

### Post by rekahsoft on 2006-09-09
I tried rythembox but was not a fan...but was very impressed with Listen...i am just having a minor issue that i need to fix (mentioned in my previous post on this page)

---

### Post by Juippisi on 2006-09-09
There were times when I used Amarok in Gnome. Now I know that it's wrong.

When I found Banshee, I fell in love immediately. I've been using Amarok since version 1.2.6 (to 1.4.2) so I was hooked up for some time. 

I do not know why this is, but I don't mind. Banshee is nice. 

I have a working podcast-plugin (from the package banshee-official-plugins) and it hasn't stopped working yet. Also to those who don't like the time that importing music takes, just go grab some coffee. It should be quite done when you come back, if Banshee hasn't crashed (there has been some problems with the CVS version).

I've also tried MPD / gMPC, Muine, Beep-media-player, XMMS, BMPx, Eclair and Listen.

---

### Post by rekahsoft on 2006-09-09
I was using banshee but am not impressed with how the GUI freezes when going to my library and searching, switching playlists etc...I like banshee too but it is just to slow for my music library (which is about 40gb)...I really like Listen just for some reaon it won't download podcasts...i can subscribe to the feeds but it doesn't download them. Anyboidy know how to fix this?

---

### Post by rekahsoft on 2006-09-09
I believe i narrowed down the problem to the fact that i enabled the unstable repos so i am running Listen 0.5 beta 1 and it is a bug of some sort...

edit: i just verified that i am running the 0.5 beta 1 version

---

### Post by flargen on 2006-09-09
Honestly, what's wrong with Rhythmbox? It takes like 2 seconds to load my ~20GB, does podcasts, portable players etc and it uses GTK. The only thing it doesn't do is videos.

---

### Post by bullon on 2006-09-09
i use totem-xine for all movies and dvds, and quod libet for music, it lets you manage yourlibrary as you want! quod libet rocks!

---

