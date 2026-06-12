---
title: "Managing Music Library"
date: 2008-03-15
forum: General Help
---

### Post by hairshirt on 2008-03-15
Hi All,

I have just built a new machine that I plan to use as the fun and games machine for the household ... you know the sort of thing, web surfing for the missus, to play music and use mythtv (when I can the damned remote control to work the way I want it to work and to use all the buttons (this is very frustrating)) no good expecting the wife to use a keyboard and mouse to use the tv.

System spec as follows:

Ubuntu 7.10 64
AMD 64 x2 4000+ something
4GB of RAM
2 x 500GB Hard Drives
All sitting on a ASUS M2N-SLI Deluxe M/Board (ok but wouldn't buy another one as for some my 800 RAM is now work as single channel).
Use twinview to control 42inch phillips tv and monitor which works ok.

I have a music library of 19272 tracks = 67 days of music.

Does anyone have any ideas of how best to manage my collection.  Until now I've been using Amarok which is quite good but I feel duty bound to use Rhythmbox.  I keep getting errors: "MIME type could not be identified" and I'd like to edit the tags.  Is rhythmbox really that good?  Amarok seems a lot better to me.

I'd be grateful for any and all tips out there on making the most of this.

Thanks in advance for any help and advice.

---

### Post by talsemgeest on 2008-03-15
Take a look here: [https://answers.launchpad.net/ubuntu/+source/rhythmbox/+question/5861](https://answers.launchpad.net/ubuntu/+source/rhythmbox/+question/5861)

Hope this helps :)

---

### Post by hairshirt on 2008-03-15
thanks, I'll have a good look

---

### Post by hairshirt on 2008-03-15
Can't seem to get gstreamer0.10-pitfdll installed

I've tried:  sudo dpkg -i --force-all gstreamer0.10-pitfdll but, of course that's for deb files

??

---

### Post by talsemgeest on 2008-03-15
Either install it with synaptic or go:
```
sudo apt-get install gstreamer0.10-pitfdll
```And you should be good

---

### Post by hairshirt on 2008-03-16
I know what you mean ... I tried both of those options but I get:  E: Couldn't find package gstreamer0.10-pitfdll

Here's my sources list:

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

##Universe

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## Multiverse

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Backports

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Canonical Partner Repository 

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free

As you can see universe is enabled. It's probably because I'm using the 64 bit OS.

Thanks for your help.

---

### Post by talsemgeest on 2008-03-16
Have you installed all of the codecs?

---

### Post by hairshirt on 2008-03-16
yes, all the codecs have been installed ... in fact everything is install and good apart from this little problem and mythtv (because of the remote control problem)

Thanks for your assistance, once again.

---

### Post by Ub1476 on 2008-03-16
Have you tried "Quod Libet"? Very slick and fast music player. Lots of different interfaces to view your music as well. "Listen" is rather cool too. 

If you want to use Rhythmbox, have you searched for gstreamer in Synaptics and tried to install those available?

---

### Post by hairshirt on 2008-03-16
Thanks ... I'll have a look at Quod Libet.

It very hard to control such a large audio library unless you do it right from the very start ... shame is, I didn't/haven't

Thanks again

---

### Post by hairshirt on 2008-03-16
have just installed Quod Libet and it can't seem to load my music collection ... lol ... good start

hang on a second ... it's doing something now ... told it to refresh the library!

---

### Post by hairshirt on 2008-03-16
OK added my music folder and refreshed ... no good ... I'll have a fiddle with it but it seems rather basic! But the plugins look quite good ... should be good for editing the tags ... very good in fact

---

### Post by Ub1476 on 2008-03-16
Music>Preferences>Library>Choose Path

Music>Reload library (they should rename this to scan..)

View>Album list

I like to use the Queue as well, but up to you (view Queue, "add songs to queue).

It took it 20-30 seconds to fetch 1,3k songs from my external HDD.

Remember to use some plugins as well (fetch album cover from Amazon, multimedia keys, burn to cd etc..)!:)

---

### Post by hairshirt on 2008-03-16
Now why the heck didn't that work when I did it ... perhaps I reload the library

Anyway, it seems o be loading the library now.

I still haven't got gstreamer0.10-pitfdll installed.

Thanks again to you both

---

### Post by hairshirt on 2008-03-16
OK did all that ... told me it was scanning with the progress bar moving left to right ... took a while and then nothing ... none of my music listed

Any ideas?

PS. Each time I've directed the prog to my music library and click apply the box just sit there .. all lazy and doing nothing!

---

### Post by Ub1476 on 2008-03-16
I uploaded a picture of my settings. Have you looked around in "view"?

---

### Post by hairshirt on 2008-03-16
Right got it ... went to view > file system

Thanks

---

### Post by unutbu on 2008-03-16
To install gstreamer0.10-pitfdll, try the update command first:

```

sudo apt-get update
sudo apt-get install gstreamer0.10-pitfdll

```

---

### Post by hairshirt on 2008-03-16
No luck with that ... sorry

---

### Post by unutbu on 2008-03-16
Ah, sorry, I forgot you mentioned you're running 64bit.
As you can see,
[http://gb.archive.ubuntu.com/ubuntu/pool/universe/g/gstreamer0.10-pitfdll/](http://gb.archive.ubuntu.com/ubuntu/pool/universe/g/gstreamer0.10-pitfdll/),
there is no 64bit deb. 

If you search and/or post in the "x86 64-bit Users" forum, they might have a solution for you.

---

### Post by talsemgeest on 2008-03-16
Ok try this for me:

```
sudo apt-get install -f
```

---

### Post by hairshirt on 2008-03-16
I've tried that ... you may recall my mentioning that earlier.  This is driving my nuts.  Started a tread in the 64bit forum but answers yet.

Back to the drawing board

---

### Post by hairshirt on 2008-03-16
> **Ub1476 said:**
> I uploaded a picture of my settings. Have you looked around in "view"?

Where did you get the skin from Ub1476?  I like the look of that.  And is that gDesklets running on the desktop.  And what desktop theme is that you have running?

Questions Questions

---

