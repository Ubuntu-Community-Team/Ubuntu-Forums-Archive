---
title: "couple of RSS + medica client questions."
date: 2007-07-20
forum: General Help
---

### Post by Darth_tater on 2007-07-20
I listen to sevral podcasts that are featured on a number of rss feeds.  every torrent client i have tired has not been perfect, it will do most of thin things i need it to, but there is always one small thing that 'breaks' the client for me.

i need a client that can handle multiple RSS feeds; the rules for how each one is processed dosent matter as long as the client can match regular expressions.   **** IMPORTANT **** i need a client that supports per feed download destination.  Example:  anything, and only anything that matched the regular expression "diggnation"is to be saved in /home/usr/podcasts/diggnation/. 

the majority of clients let me specify *one* download directory for *all* torrents.  this wont work.


also, this client must have plug in support (mandatory peer guardian block list support...)

also, a webUI is a must, as this client will run on a headless box, so remote management is a must!!!

lastly, the ability to have the client scan a/multiple directory(s) for torrent files and save them to that same directory.  EG: /home/bob/torrents has 2 torrents in it.  i want the client to scan that directory, and losd the torrents.  the location where the torrent was found should be the location that the downloaded files will get saved.


i know there has to be a client out there that can accommodate all those needs (they really aren't all that special) but everyone that i have tired does *most* but not all of the things that i would like it to do.

i have ranked the desired features in terms of "must have"



PS: yes, it sounds like ill be using Azureus for all of this, but i have a  few complaints about Azureus:

1) its slow and chews a lot of memory... thats not a good thing for this server (.9 ghz athalon 1/ 512 ram)
2) Azureus's plugin installer doesn't show up in ubuntu ( its a known bug) and installing plugins the manual way is a PITA

3) azureus will start the RSS download just like it's supposed to, but it preallocates the file in the directory where it is supposed to be saved, leading the user to think that the file is already done when in fact the file may not even be 2% done downloading!!  there is an option to have a temp folder, then copy the completed download once it has finished... but this doesn't work with the per RSS filter rule download directory

Phew!! i know that was along post (and its late for me... so there will probably be typos :( ).  I know that there are probably some things posted above that are very unclear, and if you post back i will be more than happy to clear anything up. 

thanks for any help you can provide me with.

---

### Post by tbroderick on 2007-07-21
> **Darth_tater said:**
> I listen to sevral podcasts that are featured on a number of rss feeds.  every torrent client i have tired has not been perfect, it will do most of thin things i need it to, but there is always one small thing that 'breaks' the client for me.


I'm a little confused. Are your podcasts download through a torrent or a direct download from a server?

---

### Post by Darth_tater on 2007-07-21
the RSS feeds are for torrents

RSS --> torrent --> client --> file --> me

---

### Post by tbroderick on 2007-07-21
> **Darth_tater said:**
> the RSS feeds are for torrents

RSS --> torrent --> client --> file --> me

Ah. I have no idea then :). Maybe torrentflux. Haven't used it though. I'm a rtorrent user.

---

### Post by Darth_tater on 2007-07-21
rtorrent is very basic, so i cant use it :/

and i did try torrentflux, but the apache+mysql+php is a greater security risk than i want -- not ot mention the overhead that comes from all the extra processes that are running.

i also had a few other problems with torrentflux, specifically the RSS feeds.  RSS is a *must* for me so ill keep looking arround; i get the feeling that i may have to learn how to write my own azureus plugins :(

---

