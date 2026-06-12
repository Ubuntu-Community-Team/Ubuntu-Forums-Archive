---
title: "Rhythmbox &quot;fingerprint&quot; obtain song info functionality not working in 14.04"
date: 2014-09-02
forum: General Help
---

### Post by Last_Ship on 2014-09-02
The "fingerprint" functionality of the Rhythmbox LastFM plugin worked perfectly in 12.04. The installation instructions are here: [http://askubuntu.com/questions/171989/get-track-information-from-internet-in-rhythmbox](http://askubuntu.com/questions/171989/get-track-information-from-internet-in-rhythmbox)

I've followed these instructions in 14.04, just as I did in 12.04, to no avail. I'll note that I have a clean installation of Trusty Tahr, not an upgrade. 

Here is what i'm seeing when trying to enable to plugin: [http://min.us/i/bg32LQJoiDiUX](http://min.us/i/bg32LQJoiDiUX)

Does anyone currently have the "fingerprint" Rhythmbox plugin working in 14.04, or know of a alternative? I'm just trying to have Rhythmbox (or an equivalent) identify track automatically for songs and albums.

---

### Post by Last_Ship on 2014-09-03
update: I removed the Rhythmbox plugins and reinstalled using this repository [http://xpressubuntu.wordpress.com/2013/10/26/installing-rhythmbox-3-0-plugins-the-easy-way/](http://xpressubuntu.wordpress.com/2013/10/26/installing-rhythmbox-3-0-plugins-the-easy-way/) with the same results

---

### Post by Last_Ship on 2014-09-04
I have to imagine others are having this problem as well. Identifying track information should be a pretty straight forward function. Always worked without any issues in 12.04. I'd be open to using another application if it ships default. I think Banshee also has/had this function standard.

---

### Post by Last_Ship on 2014-09-13
is there anyone for whom Rhythmbox' fingerprint function works in Trusty?

---

### Post by Last_Ship on 2014-09-14
Or maybe the better question is, can anyone confirm that the LastFM plugin works for Rhythmbox in Trusty? Again, here is what I get, after installing the plugins as per [here]("http://askubuntu.com/questions/171989/get-track-information-from-internet-in-rhythmbox") and [here]("http://xpressubuntu.wordpress.com/20...-the-easy-way/"): [IMG]http://minus.com/i/j6ADA48COIVt[/IMG] 
[http://minus.com/i/j6ADA48COIVt](http://minus.com/i/j6ADA48COIVt)[URL="http://minus.com/i/j6ADA48COIVt"]
[/URL]

I've also tried using Picard to fingerprint songs as detailed here [http://musicbrainz.org/doc/AcoustID](http://musicbrainz.org/doc/AcoustID) 
With that, I receive the following error:

E: 140310312318784 11:29:17 Fingerprint calculator failed error = No such file or directory (0)

I've got Python 2.7.6 and (i think) Python 3 installed as well. Not sure if the Picard error is stemming from the same problem that Rhythmbox is having. If not, disregard, I don't want to complicate this unnecessarily. 
[URL="http://minus.com/i/j6ADA48COIVt"]

[/URL]

---

### Post by davidmohammed on 2014-09-30
The LastFM Plugin has not received any updates from its author for quite a while - it is certainly not python3 compatible.

It needs a little bit of work to make it python3 and RB3 compatible - suggest, fork and fix.  The original project is here: [https://github.com/asermax/lastfm_extension](https://github.com/asermax/lastfm_extension)

---

### Post by Last_Ship on 2014-10-04
thank you

---

