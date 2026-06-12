---
title: "Can't watch Youtube vids."
date: 2015-08-06
forum: General Help
---

### Post by Owen Thomas on 2015-08-06
I have just discovered that I can no longer watch Youtube videos. What's happened?

I am running Ubuntu 14.4, and Firefox 39.0 on my HP laptop.

---

### Post by monkeybrain20122 on 2015-08-06
Please be more specific if you want help.

---

### Post by leunam12 on 2015-08-06
Firefox is not playing very well with flash now. I am experiencing problems also.

---

### Post by howefield on 2015-08-06
> **Owen Thomas said:**
> I have just discovered that I can no longer watch Youtube videos. What's happened?

Try switching to html5 which seems to work on many if not most videos.

[www.youtube.com/html5](www.youtube.com/html5)

---

### Post by monkeybrain20122 on 2015-08-06
In what way is Firefox not playing well with flash? Please give a description rather than some vague info to the effect of "I have a problem". 

HTML5 will kick in on Youtube if you disable flash. But here is an even better way without flash which works for many sites besides Youtube.

[https://addons.mozilla.org/en-uS/firefox/addon/watch-with-mpv/](https://addons.mozilla.org/en-uS/firefox/addon/watch-with-mpv/)
Set flash to "ask to activate" instead of disable so the html5 player will not start automatically on Youtube.

To use the addon you need up to date mpv and youtube-dl
mpv from [https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media](https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media)
and youtube-dl from
[https://launchpad.net/~nilarimogard/+archive/ubuntu/webupd8](https://launchpad.net/~nilarimogard/+archive/ubuntu/webupd8)

---

### Post by Owen Thomas on 2015-08-06
It was frustrating to see this appear, but I've apparently fixed it. The problem appeared to be with Firefox's configuration parameters being progressively perverted by the machinations of competing technologies (Adobe v HTML5 or some such).

I was perhaps terse with my initial posting because I don't care to have this problem. However, I am sure competitors' duelling will blight me with similar problems, so I suppose I'll let people know of any future frustrations in a similar way. If a future problem continues to blight me, I will give more information in the search for a remedy until the blight goes away.

Thank you to those who offered informative leads. These are appreciated, although in this instance, it appears they did not have to be followed.

---

### Post by leunam12 on 2015-08-07
> **monkeybrain20122 said:**
> In what way is Firefox not playing well with flash? Please give a description rather than some vague info to the effect of "I have a problem". 

In some websites videos don't play at all, all I get is a black box. On other websites where flash works flash block does not work, videos simply start playing . On other websites it takes a really long time for flash to load: I get a sign that says that I need a plugin to play the video while the indicator on the tab is spinning and then, after some time, it loads and the sign goes away and the video starts. I don't have any of those problems with Chrome. On other sites I can't even see the video box.

---

### Post by Owen Thomas on 2015-08-07
Truth be known, I'm still having what appears to be some complications. I too get the sign that says that I need a plugin when watching some (not all, but perhaps the more recent) Youtube stuff, but this goes away after a few seconds, and the vids start... I am blissfully unaware if this is due to Flash or some other thing, but perhaps these symptoms are relevant to readers.

---

### Post by leunam12 on 2015-08-07
Ok, I think I solved my problems by installing the freshplayerplugin. So far everything is working as it should.

---

### Post by sgian on 2015-08-07
I have a problem too with youtube in both chrome and firefox after a recent update to Ubuntu 14.04.  This is on all 5 of my computers running ubuntu 14.04 LTS, the only way to watch youtube for us is to boot into the windows partitions.  My boys noticed this a couple of days ago, and I couldn't figure it out.  It is some sort of DNS error that my page gives after trying to load for a while.  The DNS error says that the network is not configured properly, or the firewall is blocking the site, and so on.  Other webpages that I've tried work fine.  I hope this gets fixed.

---

### Post by sgian on 2015-08-08
I think this might have something to do with python and/or javascript.  Youtube uses both apparently.  I was going to file a bug report at launchpad and had to run the command 
sudo apt-get install python-apport
which installed a bunch of python stuff.  I had youtube trying to load in a browser at the same time, and it suddenly loaded after the python update and extras were installed and allowed me to watch some videos.  It doesn't work all the time, but it is an improvement on the 2 computers I've tried this on.  I have three computers to still work on.  Maybe someone who is more knowledgeable than me can narrow it down more?

---

### Post by sgian on 2015-08-10
For me it was the router, in case anyone comes across this thread looking for a solution.  I updated the firmware for the router to the latest version, and now my kids can stream youtube videos as much as they want.

---

