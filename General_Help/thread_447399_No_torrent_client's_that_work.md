---
title: "No torrent client's that work"
date: 2007-05-17
forum: General Help
---

### Post by strixy on 2007-05-17
Using Applications > Add/Remove, there are three torrent clients that are available for Ubuntu 7.04 - Azureus, Ktorrent and BitTornado.

None of them work.

**Azureus** has an issue with Java. Even after following the advice on these forums, it still crashes immediately after opening and I've spent weeks already trying to get it to work. I'm done with it. I'm never going near it again.

**Ktorrent** kills my network connection to the point that I have to power down completely. By completely I mean I have to shutdown and then turn off the power bar. I'm told that the version works, but I fail to see why I should be compiling source when it's supposed to be available from the repo's.

**Bit Tornado** works I think, but I can't get Firefox to download any of the .torrent files. It won't download because FireFox doesn't know what to use to open .torrent files anymore. I'm told I need to change my preferences in FireFox, but that doesn't work as there is no existing preference for handling .torrent files and I can't add one with Firefox. I've gone through pages and pages on this forum and the FAQ and the community doc's etc... nadda. Again, tired of trying.

What the???

The only client anyone seems to have any reported success with is Transmission - which is not natively available in Ubuntu 7.04 nor have I ever head of it before and it's not even out of beta yet.

Am I the only one who thinks something weird is going on here? Is anyone brave enough to tackle this problem to the core of the repository so we can start using at least one torrent client you know, so "it just works"? Right now, this situation is leaps and bounds away from working. 

The more I use 7.04 the more I think I'm using a beta release. What's up with that? I've been using Ubuntu since 5.10 and this is the buggiest release ever.

It must be all that proprietary software.

---

### Post by dpar on 2007-05-18
Ktorrent IS in the repos and it and Azureus both work fine on my machine, although I get much better download speeds from Ktorrent. I had to open a port for both in iptables and my router as well in order to get good download speeds. Other than that info, I'm afraid I can't help you much. I don't have the in depth knowhow.:(

---

### Post by headcronie on 2007-05-18
I've only played with Azerus on Feisty.  You're quite right.  It crashes often, and it's a PITA to get functioning again.  I've given up on it as well.

What really gets my goat is that I can't get limewire or frostwire to work at all.  They load up, connect, search, but fail to download a single thing.

I've even moved my machine to the DMZ and still nothing.  That's just flat out dumb.  Amule didn't work either.

---

### Post by shen-an-doah on 2007-05-18
I had the problem of Azureus crashing on start-up, I installed Java 6 and the version of Azureus from sourceforge (apparently the version in the repos is buggy).

[Installing Java 6](http://ubuntu1501.blogspot.com/2007/05/installing-java-runtime-environment-6.html)
[Azureus at sourceforge](http://sourceforge.net/project/showfiles.php?group_id=84122)

Before that I used Freeloader, which was pretty straightforward.

---

### Post by dpar on 2007-05-18
Have you set up iptables to allow the ports that they are using? All port are blocked by default.
Download Firestarter from the repos and use it to allow the ports.

---

### Post by headcronie on 2007-05-18
Oh... I didn't see that when I was searching for troubleshooting with Frostwire.  I'll have to look at that... once I can get my video card working.  :(

Thanks for the info.

---

### Post by sonofusion82 on 2007-05-18
Ktorrent works fine with me!
I used to use Azureus with Sun JRE but but KTorrent more responsive and faster downloads.

---

### Post by zvacet on 2007-05-18
When you download torrent file with Firefox use option **save to disc**.You can try utorrent with wine.Works good for me.

---

### Post by strixy on 2007-05-18
> (apparently the version in the repos is buggy).

That's what I'm talking about for all three of them.

> When you download torrent file with Firefox use option save to disc.

You mean right click and "save as"? Yeah, that's fine with me for some sites, but some sites have to stick their content inside java or flash - just another sign that management and marketing  shouldn't ever be allowed to have any input on the design of their websites. Who does that anymore anyway and how many books and white pages need to be written to get them to stop doing that? /rant

> You can try utorrent with wine.Works good for me

That's a little outside my point, which is simply that there are no working torrent clients available in the repos "that just work". There appears to be an issue or bug for some or most users depending on the package that you can or can't get working with or without a little this or that patch or fix or workaround or what-have-you. Again, my point is that with Ubuntu, isn't that sort of thing supposed to be resolved? taken care of? working? Isn't that one of the key advantages of using Ubuntu over other Linux distros?

---

### Post by jallain on 2007-05-18
I, too, am successfully using ktorrent. As mentioned above, you must open up the ports you are using with firestarter (download from repos) and if you are using a router, you must open those up as well. I remember something from prior use of Azereus that it suggested limiting uploads to 20k. I was doing that with ktorrent as well and my downloads were horrible. I took away the upload limit and my downloads took off like a scalded dog.So, bottom line. ktorrent seems to work very well. The only odd thing is that over time, the longer my machine has been up (not unusual with torrents) it starts to become very sluggish.

---

### Post by strixy on 2007-05-18
Until I can write up a complete compilation of advice, fixes, patches and trends in the what seems to be an endless nightmare with .torrents and Ubuntu I'll simply list some URL's I've found handy thus far. For anyone who might like to save some time, here are just a few of the threads in this forum that deal with .torrent clients and ubuntu. 

I'll do a complete write up on this topic over the long weekend.


[http://ubuntuforums.org/showthread.php?t=436499](http://ubuntuforums.org/showthread.php?t=436499)

[http://ubuntuforums.org/showthread.php?t=232638](http://ubuntuforums.org/showthread.php?t=232638)

[http://ubuntuforums.org/showthread.php?t=447277](http://ubuntuforums.org/showthread.php?t=447277)

[http://ubuntuforums.org/showthread.php?t=447790](http://ubuntuforums.org/showthread.php?t=447790) (Java issue, which is dep for Azureus).

[http://ubuntuforums.org/showthread.php?t=447700](http://ubuntuforums.org/showthread.php?t=447700)

[http://ubuntuforums.org/showthread.php?t=438750](http://ubuntuforums.org/showthread.php?t=438750)

[http://ubuntuforums.org/showthread.php?t=417180](http://ubuntuforums.org/showthread.php?t=417180)

[http://ubuntuforums.org/showthread.php?t=445600](http://ubuntuforums.org/showthread.php?t=445600)

[http://ubuntuforums.org/showthread.php?t=445185](http://ubuntuforums.org/showthread.php?t=445185)

[http://ubuntuforums.org/showthread.php?t=445090](http://ubuntuforums.org/showthread.php?t=445090)

[http://ubuntuforums.org/showthread.php?t=444096](http://ubuntuforums.org/showthread.php?t=444096)

[http://ubuntuforums.org/showthread.php?t=442255](http://ubuntuforums.org/showthread.php?t=442255)

[http://ubuntuforums.org/showthread.php?t=430952](http://ubuntuforums.org/showthread.php?t=430952)

[http://ubuntuforums.org/showthread.php?t=441632](http://ubuntuforums.org/showthread.php?t=441632)

[http://ubuntuforums.org/showthread.php?t=440008](http://ubuntuforums.org/showthread.php?t=440008)

[http://ubuntuforums.org/showthread.php?t=438704](http://ubuntuforums.org/showthread.php?t=438704)

[http://ubuntuforums.org/showthread.php?t=425024](http://ubuntuforums.org/showthread.php?t=425024) (Beagle specific)

[http://ubuntuforums.org/showthread.php?t=432101](http://ubuntuforums.org/showthread.php?t=432101)

[http://ubuntuforums.org/showthread.php?t=432616](http://ubuntuforums.org/showthread.php?t=432616)

[http://ubuntuforums.org/showthread.php?t=338596](http://ubuntuforums.org/showthread.php?t=338596) (another rant like mine here)

[http://ubuntuforums.org/showthread.php?t=431717](http://ubuntuforums.org/showthread.php?t=431717)

[http://ubuntuforums.org/showthread.php?t=430011](http://ubuntuforums.org/showthread.php?t=430011) (utorrent under wine)

[http://ubuntuforums.org/showthread.php?t=384471](http://ubuntuforums.org/showthread.php?t=384471) (firefox & .torrent specific)

[http://ubuntuforums.org/showthread.php?t=429166](http://ubuntuforums.org/showthread.php?t=429166)

[http://ubuntuforums.org/showthread.php?t=429598](http://ubuntuforums.org/showthread.php?t=429598)

---

### Post by edu77pose on 2007-05-22
Thanks for the comments, i used several of the torrent interfaces azureus, deluge and torrent flux (which was really weird setting up) but I read this about Ktorrent and it works like a treat. It is power hungrary though (don't know why) and it's got that KDE interface (gnome kicks but!) but it's working and downloading and you can close the program and start it again without any fuss, the others kept crashing once you started to download something.  

Please bring a gnome interface torrent that's as good as Ktorrent!

---

### Post by DoktorSeven on 2007-05-22
Given that torrents upload from you as well as download, you *do* need to limit your upload rate in your client to just under your maximum upload rate to your ISP, or uploads will saturate your bandwidth to the point where downloads will suffer as well. Low upload limits won't limit the download rate too much (not as much as some people says it does!).  

I always recommend ktorrent; it seems to be the best torrent program for Linux as far as features and stability is concerned.

---

### Post by Hallvor on 2007-05-23
> **DoktorSeven said:**
> 
I always recommend ktorrent; it seems to be the best torrent program for Linux as far as features and stability is concerned.

I have to disagree with that: Features, perhaps. As for stability, I doubt that it is more stable than the vanilla bittorrent client, bittornado and a couple of other lightweight clients.

---

### Post by DoktorSeven on 2007-05-26
Well, meaning features + stability, not necessarily each separate.

---

