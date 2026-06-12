---
title: "Problem With Utorrent"
date: 2007-08-10
forum: General Help
---

### Post by amyfan on 2007-08-10
i use utorrent to download my torrents and as of since yesterday when i installed beryl and emerald the utorrent icon will show at the top of the toolbar i click hide show utorrent and it wont show i tried to uninstall it but whne i did sudo apt-get remove utorrent it came back and said not utorrnet file is available to remove i used 
 that link as the guide to install it i even reinstalled it thinking it was a mess up but it done the same thing i can not get it to show up only on the tool bar by the clock and now it wont even download anything i have to use bittorrent downloader but i dont like that one i love utorrent any one have any ideas

---

### Post by amyfan on 2007-08-10
ok nvm now i gave up and am now using ktorrent it seems better with beryl =D and some other things so no need for the help now

---

### Post by Steveway on 2007-08-10
You could also try out deluge.
It's very nice and integrates better with your other GTK-apps than Ktorrent.

---

### Post by yellowband on 2007-08-10
i have the same problem with utorrent (with wine) and beryl.  If you minimize your other windows and click the utorrent icon in your taskbar, it will open up.  

I recently moved on from utorrent as well.  I have torrentflux up and running on my web server, and its great.  I love the control over torrents, adn the ablity to queue something up from anywhere on the internet (i.e. at work :) ).

---

### Post by AlexThomson_NZ on 2007-08-10
This is a long standing issue with uTorrent under Wine which I encountered too.

I use deluge now- much nicer!

---

### Post by satkata on 2007-08-10
I agree with the others.

Try out deluge. 
[http://deluge-torrent.org/downloads]("http://deluge-torrent.org/downloads")

A new version 0.5.4.1 has been just released and has got many improvements.

---

### Post by hebetude on 2007-09-03
Deluge keeps crashing for me, at least while using it through VNC.

I'm having another problem with uTorrent, huge memory usage.  Clearly something is wrong in my Top, I'm using 6g of memory in 4gig of available(1gig ram 3gig swap).

top - 16:33:29 up 1 day,  3:36,  2 users,  load average: 0.87, 0.64, 0.48
Tasks: 104 total,   2 running, 102 sleeping,   0 stopped,   0 zombie
Cpu(s): 23.3%us,  3.0%sy,  0.0%ni, 71.7%id,  1.0%wa,  0.0%hi,  1.0%si,  0.0%st
Mem:   1035744k total,  1001888k used,    33856k free,    32428k buffers
Swap:  3028212k total,      216k used,  3027996k free,   800684k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 8256 drew      18   0 2677m  19m  11m S  6.7  1.9   0:02.76 uTorrent.exe
 8260 drew      18   0 2667m  10m 5924 S  0.0  1.1   0:00.43 explorer.exe
 4490 root      15   0  173m  24m  13m S 19.3  2.4  21:08.29 Xorg

---

### Post by hebetude on 2007-09-15
> **hebetude said:**
> Deluge keeps crashing for me, at least while using it through VNC.

I'm having another problem with uTorrent, huge memory usage.  Clearly something is wrong in my Top, I'm using 6g of memory in 4gig of available(1gig ram 3gig swap).

top - 16:33:29 up 1 day,  3:36,  2 users,  load average: 0.87, 0.64, 0.48
Tasks: 104 total,   2 running, 102 sleeping,   0 stopped,   0 zombie
Cpu(s): 23.3%us,  3.0%sy,  0.0%ni, 71.7%id,  1.0%wa,  0.0%hi,  1.0%si,  0.0%st
Mem:   1035744k total,  1001888k used,    33856k free,    32428k buffers
Swap:  3028212k total,      216k used,  3027996k free,   800684k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 8256 drew      18   0 2677m  19m  11m S  6.7  1.9   0:02.76 uTorrent.exe
 8260 drew      18   0 2667m  10m 5924 S  0.0  1.1   0:00.43 explorer.exe
 4490 root      15   0  173m  24m  13m S 19.3  2.4  21:08.29 Xorg

Just for reference, I now use rTorrent+dtach which lets me ssh in start rtorrent (or check rtorrent) then hit a key to release rTorrent from my session (and continue to run in the background whether or not I'm logged in).

---

