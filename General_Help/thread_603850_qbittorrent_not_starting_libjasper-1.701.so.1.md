---
title: "qbittorrent not starting libjasper-1.701.so.1"
date: 2007-11-05
forum: General Help
---

### Post by AngryAnimal on 2007-11-05
Gutsy
qBittorrent v1.0.0rc7
NewBie

Received update 4th November for qBittorrent and some libtorrent thingy - installed as always, on with the brave.  Tried to start qBittorrent and nothing!

went to command line and tried to execute from bin and got the following error

**error while loading shared libraries: libjasper-1.701.so.1: cannot open shared object file: No such file or directory**

found some help on the ubuntu /fr  - vive le france etc

in a terminal window type

sudo ln -s /usr/lib/libjasper.so.1.0.0 /usr/lib/libjasper-1.701.so.1

this creates a symbolic link - see man ln for more info

..long story short qBittorrent now seems to start OK.

Anybody else had problems? Not sure if this has been reported

---

### Post by goldenzim on 2007-11-05
I had exactly the same problem - qBitTorrent was working before my upgrade. Not a dist upgrade just, you know, keeping things current, and then it wasn't.

I ran 

*sudo ln -s /usr/lib/libjasper.so.1.0.0 /usr/lib/libjasper-1.701.so.1 *

and all seems cool now.

---

### Post by frc on 2007-11-06
Same problem here on two machines....qQbittorrent did not start after  update...
have been looking for solution the last couple of days....
Viva LA France....for the solution!

sudo ln -s /usr/lib/libjasper.so.1.0.0 /usr/lib/libjasper-1.701.so.1

Thanks a lot!

---

### Post by TheSe7enthSin on 2007-11-06
Thanks, this worked great.

---

### Post by apd on 2007-11-12
sry folks.. the sudo ln -s /usr/lib/libjasper.so.1.0.0 /usr/lib/libjasper-1.701.so.1 worked just fine at first but after a couple of hours i keep getting a " the download of abc.avi have been paused, Full Disc?" It doesn´t matter how many or few torrents i´m downloading. Right now it´s impossible to download a single torrent. And the log is saying "couldn´t define abc.avi as a torrent it might be damaged in some way." I´musing the using the latest version stable version of qBittorrent on Gutsy 7.10. Any suggestions ni1?

---

