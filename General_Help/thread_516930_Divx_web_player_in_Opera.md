---
title: "Divx web player in Opera?"
date: 2007-08-03
forum: General Help
---

### Post by Spaceomega on 2007-08-03
Recently got Ubuntu working with my wireless card (first since Herd 5; yay!) and I was wondering if there was possibly a way to play divx movies in Opera?

I've heard of mplayer, but I'm not sure if this works with Opera, any help?

Thanks.

---

### Post by apetresc on 2007-08-03
Google is your friend :) This is indeed possible, and in fact very easy. Check here for instructions on installing a variety of Opera plugins on Linux, including mplayer and gxine: [http://www.opera.com/linux/docs/plugins/install/](http://www.opera.com/linux/docs/plugins/install/)

---

### Post by Spaceomega on 2007-08-03
> **AdrianP said:**
> Google is your friend :) This is indeed possible, and in fact very easy. Check here for instructions on installing a variety of Opera plugins on Linux, including mplayer and gxine: [http://www.opera.com/linux/docs/plugins/install/](http://www.opera.com/linux/docs/plugins/install/)

I googled a few times, actually.  Must've not googled quite well enough.

Why, google, why? :(

Anyways, thanks.  I'll see if I can get some of those things to work.

---

### Post by apetresc on 2007-08-03
Hehe, effective Googl'ing can be a black art sometimes :) If it helps, the search term I used was "mplayer opera" and the link I posted was the very first hit from that query.

Good luck setting those up, and if something doesn't work quite right, post back here!

---

### Post by Spaceomega on 2007-08-03
Problem, I'm at the Gecko SDK step; Where do I get this Gecko SDK thing?

---

### Post by apetresc on 2007-08-03
> **Spaceomega said:**
> Problem, I'm at the Gecko SDK step; Where do I get this Gecko SDK thing?

Info on getting the Gecko SDK can be found here: [http://mplayerplug-in.sourceforge.net/install.php](http://mplayerplug-in.sourceforge.net/install.php)

---

### Post by Spaceomega on 2007-08-03
> **AdrianP said:**
> Info on getting the Gecko SDK can be found here: [http://mplayerplug-in.sourceforge.net/install.php](http://mplayerplug-in.sourceforge.net/install.php)

I feel like an idiot; I cannot figure out those instructions to save my life.

---

### Post by apetresc on 2007-08-03
> **Spaceomega said:**
> I feel like an idiot; I cannot figure out those instructions to save my life.

:( Do not feel stupid. To be honest, this is a much more complicated procedure than is normally the case. Because Opera is not open source, however, Ubuntu cannot package it, and therefore cannot support things like this. But we try our best!

Instead of compiling it yourself, try the following. I'm not sure if it'll work, but it should:

1. Install gxineplugin with "sudo apt-get install gxineplugin"
2. Type the following: ```
sudo ln -s /usr/lib/gxine/gxineplugin.so /usr/lib/opera/plugins/gxineplugin.so
```
3. Restart Opera

Try it out and see if that gets it working :)

---

### Post by Spaceomega on 2007-08-03
> **AdrianP said:**
> :( Do not feel stupid. To be honest, this is a much more complicated procedure than is normally the case. Because Opera is not open source, however, Ubuntu cannot package it, and therefore cannot support things like this. But we try our best!

Instead of compiling it yourself, try the following. I'm not sure if it'll work, but it should:

1. Install gxineplugin with "sudo apt-get install gxineplugin"
2. Type the following: ```
sudo ln -s /usr/lib/gxine/gxineplugin.so /usr/lib/opera/plugins/gxineplugin.so
```
3. Restart Opera

Try it out and see if that gets it working :)

Nope.  Not working at all.

---

### Post by apetresc on 2007-08-03
> **Spaceomega said:**
> Nope.  Not working at all.

Hm, drat. Okay, can you give me a link to the exact .deb file you used to install your version of Opera? I will install the same version here too, and see if I can work out getting the mplayer plugin to work.

---

### Post by Spaceomega on 2007-08-03
> **AdrianP said:**
> Hm, drat. Okay, can you give me a link to the exact .deb file you used to install your version of Opera? I will install the same version here too, and see if I can work out getting the mplayer plugin to work.

[http://opera.gundari.net/linux/922/final/en/i386/shared/opera_9.22-20070716.6-shared-qt_en_i386.deb](http://opera.gundari.net/linux/922/final/en/i386/shared/opera_9.22-20070716.6-shared-qt_en_i386.deb)

It's from Opera's site.

---

### Post by apetresc on 2007-08-03
> **Spaceomega said:**
> [http://opera.gundari.net/linux/922/final/en/i386/shared/opera_9.22-20070716.6-shared-qt_en_i386.deb](http://opera.gundari.net/linux/922/final/en/i386/shared/opera_9.22-20070716.6-shared-qt_en_i386.deb)

It's from Opera's site.

Alright, thanks, I'll get on it right now, and post back here if I get anywhere.

Do you have a particular video you've been using to test this?

---

### Post by Spaceomega on 2007-08-04
> **AdrianP said:**
> Alright, thanks, I'll get on it right now, and post back here if I get anywhere.

Do you have a particular video you've been using to test this?

[http://www.tv-links.co.uk/video/4/6116/9493/59600/84215](http://www.tv-links.co.uk/video/4/6116/9493/59600/84215)

I tried a few on apple's site in the trailer section as well.

---

### Post by apetresc on 2007-08-04
Okay, success :) The trick was to install ```
adrian@adrian-desktop:~$ sudo apt-get install mozilla-mplayer
```
It turns out that Opera can read Mozilla plugins, and in fact does so by default. To make sure, after you've installed that package and restarted Opera, go to "Tools->Preferences->Advanced->Content->Plug-in Options" and make sure it looks like this: [http://komrades.org/screenshots/operaprefs.png](http://komrades.org/screenshots/operaprefs.png)

If you don't have all those entries, particularly the DivX one, add the part that I've highlighted in my screenshot to the path there, to make sure it's checking the Firefox plugin directories.

Good luck :)

---

### Post by Spaceomega on 2007-08-04
> **AdrianP said:**
> Okay, success :) The trick was to install ```
adrian@adrian-desktop:~$ sudo apt-get install mozilla-mplayer
```
It turns out that Opera can read Mozilla plugins, and in fact does so by default. To make sure, after you've installed that package and restarted Opera, go to "Tools->Preferences->Advanced->Content->Plug-in Options" and make sure it looks like this: [http://komrades.org/screenshots/operaprefs.png](http://komrades.org/screenshots/operaprefs.png)

If you don't have all those entries, particularly the DivX one, add the part that I've highlighted in my screenshot to the path there, to make sure it's checking the Firefox plugin directories.

Good luck :)

Mine looks like [this](http://i12.tinypic.com/5y0ihpl).

Is there a way to ... change what I have with what you have?

---

### Post by apetresc on 2007-08-04
> **Spaceomega said:**
> Mine looks like [this](http://i12.tinypic.com/5y0ihpl).

Is there a way to ... change what I have with what you have?

What is the output of the following command on your computer? ```
ls /usr/lib/mozilla/plugins
```

While looking around I found this page here: [https://help.ubuntu.com/community/OperaBrowser](https://help.ubuntu.com/community/OperaBrowser)

If you look at the bottom it says: > As of now (May 2007), embedded video playback does not work well in opera. The probably best plugin, mozilla-mplayer, works only partialy and requires [WWW] manual compiling. You can try vlc, gxineplugin or totem, but it is probably adviseable to just use Firefox for sites as [WWW] [http://www.apple.com/trailers](http://www.apple.com/trailers)
I tested on the Apple site and it worked, but I guess it will not work everywhere judging by that excerpt. :(

---

### Post by Spaceomega on 2007-08-04
> **AdrianP said:**
> What is the output of the following command on your computer? ```
ls /usr/lib/mozilla/plugins
```

While looking around I found this page here: [https://help.ubuntu.com/community/OperaBrowser](https://help.ubuntu.com/community/OperaBrowser)

If you look at the bottom it says: 
I tested on the Apple site and it worked, but I guess it will not work everywhere judging by that excerpt. :(

```
flashplayer.xpt                 libtotem-narrowspace-plugin.xpt
gxineplugin.so                  mplayerplug-in-dvx.so
libflashplayer.so               mplayerplug-in-dvx.xpt
libjavaplugin.so                mplayerplug-in-qt.so
libtotem-basic-plugin.so        mplayerplug-in-qt.xpt
libtotem-basic-plugin.xpt       mplayerplug-in-rm.so
libtotem-gmp-plugin.so          mplayerplug-in-rm.xpt
libtotem-gmp-plugin.xpt         mplayerplug-in.so
libtotem-mully-plugin.so        mplayerplug-in-wmp.so
libtotem-mully-plugin.xpt       mplayerplug-in-wmp.xpt
libtotem-narrowspace-plugin.so  mplayerplug-in.xpt
tyler@tyler-linux:~$ 
```

---

