---
title: "How to monitor the web activity ?"
date: 2014-11-19
forum: General Help
---

### Post by Innernet on 2014-11-19
Hi all.
Running 14.04 + Gnome on my own hotspot Wifi.
The System Monitor network resources and the Wifi activity light on the laptop show minor periodic activity transmitting and receiving even while inactive on the web.
It did not happen when I ran 12.04 + same everything else.
How to tell what is that traffic about ?  Can it be stopped ?  Does your compfuser behave the same ?

---

### Post by TheFu on 2014-11-19
Since 12.04 much has changed - Canonical is sending data for everything you type into the dock/dash to external websites now.  There are how-tos to disable that.  I find it easier to just stop using Unity and to purge all lens* packages.  Do a little searching on those topics to find the how-tos.
```

dpkg -l|grep lens
```
will provide ideas of these apps, though not all of those in the list are part of the problem.

---

### Post by cariboo on 2014-11-19
You can use wireshark, it's in the repositories, to monitor network activity. Use the instructions[ here]("https://ask.wireshark.org/questions/7976/wireshark-setup-linux-for-nonroot-user") to set it up, to use it as a non-root user.

---

### Post by Innernet on 2014-11-21
Thanks gentlemen.
..." Canonical is sending data for everything you type into the dock/dash to external websites now."...

Another intrusive Google ?   Am using a humble DuckDuck something instead for default searches.

..."stop using Unity"...   Am not _using_ Unity, am using only Gnome-classic, from the moment the compfuser is turned on and I log in as root  'administrator'.   But I believe it is installed as came with 14.04.  If Unity is doing this thing in the background without disclosing, please let me know how to shotgun it.
I just want to **know** what is going on.

Been running Ubuntu since 5.10... how wonderful 7.04 was.   More complexities now does not seem to justify the unnecessary bells and whistles.

This Wireshark seems promising... if I will be able to interpret/understand its reports.  And if allows me to stop the spying.

Can the "lens" thinghy be explained please ?  Or where to learn its workings/deletion ?
Is this it ? ----> [http://www.addictivetips.com/ubuntu-linux-tips/how-to-remove-a-unity-lens-in-ubuntu-linux/](http://www.addictivetips.com/ubuntu-linux-tips/how-to-remove-a-unity-lens-in-ubuntu-linux/)

This thar may be not that much trusty.

---

### Post by mikewhatever on 2014-11-22
> **Innernet said:**
> Hi all.
Running 14.04 + Gnome on my own hotspot Wifi.
...

First, running Ubuntu + Gnome on a hotspot is an unheard of fit of engeniring. You might want to share a howto. ;)

> **Innernet said:**
> Thanks gentlemen.
..." Canonical is sending data for everything you type into the dock/dash to external websites now."...

Another intrusive Google ?   Am using a humble DuckDuck something instead for default searches.

..."stop using Unity"...   Am not _using_ Unity, am using only Gnome-classic, from the moment the compfuser is turned on and I log in as root  'administrator'.   But I believe it is installed as came with 14.04.  If Unity is doing this thing in the background without disclosing, please let me know how to shotgun it.
I just want to **know** what is going on.

Been running Ubuntu since 5.10... how wonderful 7.04 was.   More complexities now does not seem to justify the unnecessary bells and whistles.

This Wireshark seems promising... if I will be able to interpret/understand its reports.  And if allows me to stop the spying.

Can the "lens" thinghy be explained please ?  Or where to learn its workings/deletion ?
Is this it ? ----> [http://www.addictivetips.com/ubuntu-linux-tips/how-to-remove-a-unity-lens-in-ubuntu-linux/](http://www.addictivetips.com/ubuntu-linux-tips/how-to-remove-a-unity-lens-in-ubuntu-linux/)

This thar may be not that much trusty.

Easy there, don't get carried away by the bashing wind. My esteemed colleague has obviously missed the fact that you don't use Unity, and everything that came thereafter was ...nonsense complete (as the French might put it). Even if Unity is installed, it wouldn't be running, also, "inactive on the web" doesn't mean the wireless card and router go to sleep. More likely than not, what you see is the router - client communication, rather then "web activity". 
I'd suggest using iftop to varify that.

Many wireless drivers have led blinking parameters, which got turned on in recent years. The outcome is, leds that never blnked before, now go crazy, unless the blinking is disabled.

---

### Post by Al1000 on 2014-11-22
tcpdump might be everything you are looking for, and it should already be installed.

```
sudo tcpdump -D
```

...will list your network devices and assign numbers to them. If the number of your wireless interface is say 2, then:

```
sudo tcpdump -i 2
```

...monitors its activity, and displays the output in the terminal (by default).

---

### Post by TheFu on 2014-11-23
> **mikewhatever said:**
> My esteemed colleague has obviously missed the fact that you don't use Unity, and everything that came thereafter was ...nonsense complete

True - I didn't assume "gnome" was gnome-classic. Does gnome3 have something like lenses too? Perhaps not.

Canonical is trying to help average people and doing web searches in the dock might be helpful to many people. Plus they can get referral income from amazon search results.  I suspect a few people are like me and want to control what data leaves our systems, but idunno.  Again, if you don't use Unity, I don't believe this is happening.

---

### Post by SeijiSensei on 2014-11-23
It could be a symptom of this bug: [https://bugs.launchpad.net/ubuntu/+source/wpa/+bug/1323089](https://bugs.launchpad.net/ubuntu/+source/wpa/+bug/1323089)

---

