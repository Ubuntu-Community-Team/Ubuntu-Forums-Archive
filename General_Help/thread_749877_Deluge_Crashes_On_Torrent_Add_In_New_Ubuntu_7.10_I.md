---
title: "Deluge Crashes On Torrent Add In New Ubuntu 7.10 Install"
date: 2008-04-08
forum: General Help
---

### Post by TheWired on 2008-04-08
I have just installed a new machine with Ubuntu 7.10 (fully patched) and ran through the steps in the FAQ on deluge-torrent.org to install the latest version of Deluge from SVN. It installs properly (so it seems) and I can run the program. However, whenever I point it towards a torrent (from the machine not the web UI) it will just close. I ran deluge from the terminal to see if it would give me some kind of error message when it crashes, but nothing.

I have searched the Support Forum and FAQ on deluge-torrent.org as well as ubuntuforums.org, but I haven't found a fix that has worked or mimics the same problem. Any help will certainly be greatly appreciated.

---

### Post by ryanhaigh on 2008-04-09
Why not try removing the svn version you have compiled and use the deb from the repos or even the deluge website? Is there some specific feature only available in the svn version?

---

### Post by kpkeerthi on 2008-04-09
Get the latest version from [here]("http://www.getdeb.net/app/Deluge"). Before sure to delete ~/.config/deluge before you start the updated deluge.

---

### Post by TheWired on 2008-04-09
I had another machine that was running Feisty that had Deluge installed from the SVN that was running fine. I decided on my new machine to try out 7.10 and break out of my comfort zone, and had actually tried the .deb in my first run, hitting a lot of dependency issues. I am pretty sure I resolved 99% of them with the SVN install though so I will try the .deb version and see how that goes.

I had chosen the SVN version just because I assumed it would be the latest stable version.

---

### Post by TheWired on 2008-04-09
I installed the same dependencies from the FAQ/SVN install to install the .deb file. I added 1 extra that Deluge was looking for. The packages I installed were: 

```
sudo apt-get install g++ make python-all-dev python-all python-dbus python-gtk2 python-notify librsvg2-common python-xdg python-support subversion libboost-dev libboost-thread-dev libboost-date-time-dev libboost-filesystem-dev libboost-serialization-dev libssl-dev zlib1g-dev python-pyopenssl

sudo dpkg -i Desktop/deluge-torrent_0.5.8.8-1_i386.gutsy.deb
```

I ran deluge from the terminal and received the following output

```
thewired@media:~$ deluge
checking for ubuntu...
found and fixing ubuntu
thewired@media:~$ checking for ubuntu...
no existing Deluge session
Starting new Deluge session...
deluge_core; using libtorrent 0.13.0.0. Compiled with NDEBUG.
Applying preferences
save uploaded memory
Pickling state...
Scanning plugin dir /usr/share/deluge/plugins
Initialising plugin BlocklistImport
Initialising plugin NetworkHealth
Initialising plugin WebSeed
Initialising plugin TorrentCreator
Initialising plugin SpeedLimiter
Initialising plugin WebUi
Initialising plugin Search
Initialising plugin MoveTorrent
Initialising plugin TorrentPeers
Initialising plugin EventLogging
Initialising plugin TorrentFiles
Initialising plugin FlexRSS
Initialising plugin TorrentNotification
Initialising plugin Scheduler
Initialising plugin DesiredRatio
Initialising plugin NetworkGraph
Applying preferences
Starting DHT...
Showing window
Found TorrentFiles plugin...
Found TorrentPeers plugin...
```

This looks all normal as it is running, however after I add a torrent to the program the GUI closes and I am left with nothing. My next debug step was deleting my saved config and trying again. I removed .config/deluge and ran Deluge from the terminal and saw this.

```
thewired@media:~$ deluge
checking for ubuntu...
found and fixing ubuntu
thewired@media:~$ checking for ubuntu...
no existing Deluge session
Starting new Deluge session...
deluge_core; using libtorrent 0.13.0.0. Compiled with NDEBUG.
Applying preferences
save uploaded memory
Pickling state...
Scanning plugin dir /usr/share/deluge/plugins
Initialising plugin BlocklistImport
Initialising plugin NetworkHealth
Initialising plugin WebSeed
Initialising plugin TorrentCreator
Initialising plugin SpeedLimiter
Initialising plugin WebUi
Initialising plugin Search
Initialising plugin MoveTorrent
Initialising plugin TorrentPeers
Initialising plugin EventLogging
Initialising plugin TorrentFiles
Initialising plugin FlexRSS
Initialising plugin TorrentNotification
Initialising plugin Scheduler
Initialising plugin DesiredRatio
Initialising plugin NetworkGraph
Applying preferences
Starting DHT...
Showing window
Found TorrentFiles plugin...
Found TorrentPeers plugin...
```

It shows that my config was removed and I had to go through the steps to create a new one. Once again the GUI would crash as soon as I add a torrent. Has anyone successfully installed and runs Deluge on a bare Gusty install? I have a test environment in a VM and my server at home both with a new 7.10 install and both are experiencing the same problems.

---

### Post by gillza on 2008-04-09
I am experiencing the same problem. Freshly installed 7.10, Deluge 5.8.8.-1 downloaded from main website. When adding a torrent it crashes... Tried building it myself from source and the same happens...

Deluge downloaded from the repositories works fine.

---

### Post by sakis on 2008-04-09
I'm having the same problem here with the latest release but on hardy (8.04). When i install the deb file from their site 0.5.8.8 and try to run the program it crashes! If i try the 0.5.8.7 version everything works fine!

---

### Post by vishzilla on 2008-04-09
Looks like many of us are having the same problem. May be a bug fix should come anytime soon!

---

### Post by Skerit on 2008-04-10
Confirmed, same problem over here!

And just as a side note; that scheduler plugin is completely worthless! *grrrrr*

---

### Post by TheWired on 2008-04-10
Did a little more research and apparently this is a known bug. See [http://forum.deluge-torrent.org/viewtopic.php?f=7&t=4455](http://forum.deluge-torrent.org/viewtopic.php?f=7&t=4455). The recommendation is to grab the 2nd latest release from [http://download.deluge-torrent.org/](http://download.deluge-torrent.org/). I will be trying it today to test if it works.

---

