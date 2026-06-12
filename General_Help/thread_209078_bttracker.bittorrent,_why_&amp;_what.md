---
title: "bttracker.bittorrent, why &amp; what?"
date: 2006-07-04
forum: General Help
---

### Post by Czar on 2006-07-04
Dear Ubuntu Users,

I am confused as to the usage of the start-up/shutdown message "bttracker.bittorrent".  [In this topic](http://www.ubuntuforums.org/showthread.php?t=163611) samir85 explains how to disable, ["sudo update-rc.d bittorrent remove"] yet before I do that, does anyone have a clue (and could share) why this service is running?

How might I use it?  What might I use it for (other then the obvious, I'm on a laptop w/ Ubuntu?)

---

### Post by OffHand on 2006-07-08
bump... I would like to know this too.
Is there anyone who can enlighten us?

---

### Post by droazen on 2006-07-10
Well, as for what its purpose is, it's a program that provides bittorrent clients with a list of the current seeders/downloaders of a particular torrent, so that it can connect directly to them & request the pieces of the torrent it needs. It's really only useful if you're hosting a .torrent file on your machine, and want to provide your own tracking service for downloaders.

However as far as I can tell, by default the bttrack.bittorrent service is not started in Dapper. There is no symlink to the /etc/init.d/bittorrent script in either /etc/rcS.d or /etc/rc2.d, which contain links to the scripts started during a typical bootup. There are links to that script in /etc/rc6.d and /etc/rc0.d (restart & shutdown), which is why you get the "stopping bittorrent tracker" message (even though it was never started in the first place :).

Also, there is a shell variable in /etc/default/bittorrent called START_BTTRACK, which is set to 0 by default. However there appears to be a bug ([https://launchpad.net/distros/ubuntu/+source/bittorrent/+bug/27654]("https://launchpad.net/distros/ubuntu/+source/bittorrent/+bug/27654")) in the /etc/init.d/bittorrent script - it fails to check the state of this variable before starting the bttrack service. So, if you made a link to /etc/init.d/bittorrent in either /etc/rcS.d or /etc/rc2.d, it would probably start regardless of the value of START_BTTRACK. But by default it is not, so it shouldn't be a concern from a security standpoint.

Hope that helps...

---

### Post by lechbialek on 2006-07-31
I noticed the service too (during shutdown) I don't think this is funny an do fear for a security issue.

If you use apt-get to remove bittorent (the application, not the rc.d entry). It says it is going to remove ubuntu too... which is a bit sad isn't it.

Lech

---

### Post by Jeef on 2006-08-05
We all know what BitTorrent is, and what a BitTorrent tracker is... What I want to know, however, is what business either of these things have on a fresh installation of Dapper. I mean, come on, why does the desktop version of Dapper need a BitTorrent tracker init script in a handful of its runlevels? Disabled or enabled, the fact that it's there is ominous. To top it off, Ubuntu does not even come with the bittorrent-gui package, so why does it even bother including the bittorrent package? I could understand someone arguing that Ubuntu comes with bittorrent to be noob-friendly, but if that's the case, explain why it doesn't come with the GUI yet it comes with the not-so-noob-friendly headless and curses versions. [-X

At any rate, when did the desktop installer ask me if I wanted peer to peer 'server-esque' software? Oh wait, it didn't... :-\"

---

### Post by [flax] on 2006-09-06
> **Jeef said:**
> We all know what BitTorrent is, and what a BitTorrent tracker is... 
.............

Nope, i dont know. Can i use this bttracker.bittorrent to download bittorrents in the background? 

In my ideal situation, i would specify a directory and place torrent files in it, afterwhich the service will download data of torrents. 

(i want my server to perform the download, while my desktop can be turned off at night)

---

### Post by marianom on 2006-09-06
We've been discusing this thing not long ago.
See if there's something there that might help:

[http://www.ubuntuforums.org/showthread.php?t=238864](http://www.ubuntuforums.org/showthread.php?t=238864)

---

### Post by [flax] on 2006-09-06
Thank you for the reply. 

I now know that the tracker has no use for me(, and also i find it quite strange that it runs as root)

Since i only want to download torrent-data, my question is still the same. Are there any services that download torrents as a service? (so i can run it on my server?)

(whith some http interface, or whatever...)

---

### Post by The Uniphobiac on 2006-09-06
Just a Note: If you remove software and it says its removing ubuntu-desktop...thats ok it won't remove your other software.  The package ubuntu-desktop is just a meta packages that depends on all the default packages so ubuntu kubuntu and xubuntu software can be installed without specifying each package.

---

