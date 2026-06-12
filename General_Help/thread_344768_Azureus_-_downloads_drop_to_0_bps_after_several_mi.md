---
title: "Azureus - downloads drop to 0 bps after several minutes"
date: 2007-01-23
forum: General Help
---

### Post by Natume on 2007-01-23
My problem of the day deals with Azureus, which has been installed and is, to the best of my knowledge completely functional (if it makes any difference, it was installed with the package manager, not from source).  I currently have three torrents running in the program, each about 200 megs, with about 100 seeds and 40 peers (not connected to all of the seeds and peers, of course).  The NAT is perfectly fine, according to both the icon in the status bar and the NAT test feature in the menu ; I've forwarded the port that I'm using in Azureus via the command line and have a script that does so on each Ubuntu startup.

For the first few minutes or so after I've started Azureus, the torrents run fine, ramping up to a normal download rate, connecting to anywhere between 5 and 40 seeds depending on the time.  However, after those first few minutes, the speed for each torrent drops off rapidly to a standstill at 0 bps (the torrents drop off separately, but at similar times - my impression is that that's because they've been started at similar times).

I'm not entirely certain why this would be happening, except for the fact that when I connect to new seeds or peers, I temporarily get a decent download speed again, until it ramps down to 0, the same as after startup of the program.  My assumption is that Ubuntu (or some part of Linux) is blocking off the seeds and peers as they try to connect, even though the port is open.  Of course, being new to Ubuntu, and Linux in general, I'm not sure of a way to test this, or fix it, if it is indeed the problem.

I should mention that the same behavior happens when seeding.  By pure luck, I managed to get one of the three torrents completely downloaded, and after it began seeding, it was seeding at about 100 kbps for a minute or so.  Just like with the downloading, however, it ramped down (and more generally, the upload speeds do the same thing as download for the torrents that aren't being seeded ; of course, having less of the file to upload, it's more consistently at 0 bps).  The other two torrents are about 50% done - the only way I've been able to do this is by restarting Linux and / or Azureus.  Seeing as there are so many seeds and peers, I'm not certain as to whether restarting allows me to get some download from the same people, or whether I'm just connecting to new people, who are subsequently blocked (if, again, that is indeed the problem).

Just ask for more info if I left anything out (providing the commands needed to obtain it, of course ^_^).  Perhaps this problem isn't exclusive to me, or if it is, maybe I'm just being stupid about it.  Either way, if anybody has some productive input, I'd be glad to hear it.

---

### Post by DJ_Peng on 2007-01-23
I had that happen to me as well a week or so ago. I couldn't find anything about it so I dumped it and went back to KTorrent. It's too bad, too, because I really wanted to get rid of the one KDE app in my GNOME enviroment.

---

### Post by 13thMonkey on 2007-01-24
I've been having the exact same problem!  I installed Ubuntu a few days ago and Azureus has been driving me up the wall - the same settings as on my old Windows box on the same tracker die after a while. Now I've got my other stuff running I thought I'd best see if there's a fix for it. Anyway, try this thread [http://ubuntuforums.org/showthread.php?t=191110&highlight=azureus](http://ubuntuforums.org/showthread.php?t=191110&highlight=azureus). It seems to be working for me.

I installed sun-java5-jre  after Azureus but it wasn't using it.

```
sudo update-alternatives --config java
```
fixed that and my torrents are back to normal (so far). If that doesn't work I'm going to try overwriting the azureus.jar file as suggested in this thread [http://ubuntuforums.org/showthread.php?t=342253&highlight=azureus](http://ubuntuforums.org/showthread.php?t=342253&highlight=azureus)

If I don't reply it's worked =D>

---

### Post by Natume on 2007-01-24
Ah ; thanks for the tips.  Haven't tried anything yet, but I'll edit this post with updates on it as I work through it (or try to and get fed up {chuckles}).

---

### Post by 13thMonkey on 2007-01-25
Just to add that I'm using 2.5.0.0 from the repositories.

Anyway, it's been running for 24 hours without any problems at all so the Sun java (also from the repositories) has fixed it.

---

### Post by Natume on 2007-02-03
Hmm... well, I've installed the Sun Java 1.5.0_8 from the repositories (tried installing from source, but the issue with that was that I wasn't sure how to make Ubuntu recognized that it was there).  The downloads are certainly going now, no NAT problems or anything, but there are still some issues with speeds dropping off.  Granted, they'll often pick up again after a while, but they seem to fluctuate up and down between 0 bps and 100 kbps.

I'll try some other torrents with more seeds as well, to see how that works ; each of these has about 5 seeds.  It's usable, but for the interim, Bittorrent was getting somewhat faster speeds.

Ah, and for the record, I'm using Azureus 2.5.0.4, after doing a couple updates to it.  Doesn't seem to make a big difference one way or the other from before the update (except that one of the torrent's trackers that I was using denied me connection on 2.5.0.2 [explicitly - it just said that it didn't allow my version of the azureus], but works on 2.5.0.4).

---

