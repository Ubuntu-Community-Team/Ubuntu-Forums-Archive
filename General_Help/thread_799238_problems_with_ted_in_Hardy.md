---
title: "problems with ted in Hardy"
date: 2008-05-18
forum: General Help
---

### Post by xeddog on 2008-05-18
I am having several problems using ted (torrent episode downloader) in Ubuntu hardy.  Having some minor problems with my other Java application too, so it might be Java.  Anyway, here are the three most annoying. 

1.  hangs - many times I will try to open the ted window by double-clicking the icon in the top panel.  It is completely unresponsive.  The only way I can kill it is to use the System monitor and end the process.  Sometimes it will hang with the window open.  One or more of the tv shows I am interested in will show as checking item so-and-so.  But I cannot end it, move the window, minimize it or anything.  Have to use the system monitor to kill it again.

2.  Once in a while I will get a torrent added to Asureus (the other Java app) that is just not anything I asked for.  Haven't added anything even close to the show in ted, but I am assuming that ted downloaded the torrent because I don't have any other app running that can do that.

3.  For some shows, ted just won't download the torrent.  I have checked the filters and modified them so that I should be getting something.  For example, I can look at Mininova and see 20 seeds for a show.  I set the filters to a minimum of 10 and decrease the minimum filesize to 1/2 of what is shown in Mininova, and it still won't download any torrents.  The log just shows no torrents found, or maybe filesize incorrect.  I can manually download a torrent from Mininova and it downloads fairly fast, and I can watch the show with no errors or other problems.

Any help with the first two especially would be appreciated.

Thanks,

xeddog

P.S.  Java build 1.6.0-b09,  Ubuntu 8.04 LTS with latest updates as of yesterday (5/17/08).

---

### Post by fiatguy85 on 2008-06-16
I found that cutting the system tray icon off in the preferences helped the stability of the program a lot.  In another thread it was giving people errors, but was not for me.  However, cutting off the icon seemed to fix the hangs for me.  Late, but hopefully helpful to someone.

---

