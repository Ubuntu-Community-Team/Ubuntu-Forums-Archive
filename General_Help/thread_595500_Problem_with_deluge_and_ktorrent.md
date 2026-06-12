---
title: "Problem with deluge and ktorrent"
date: 2007-10-28
forum: General Help
---

### Post by yvanc on 2007-10-28
My current OS is ubuntu 7.04. I have deluge and ktorrent installed. I left my pc overnight while downloading torrents. It was screen locked. When I checked on my download in the morning, my ktorrent tray icon is gone. I restarted my pc but it crashed so I used the reset button instead. When I rebooted my OS. I can't seem to start deluge or ktorrent.  I tried to reinstall them both but the behavior is still the same.

---

### Post by grantk86 on 2007-10-28
I'm not sure about deluge, but I know that the KTorrent package in the Ubuntu Feisty repositories has a bug which causes it to crash after some period of time.  You have a few basic options to fix this:

1 - Go to KTorrent website & download latest stable Debian version (2.2.2)  (<http://ktorrent.org/index.php?page=downloads>).  Uninstall the Ubuntu version first, then install the updated package.

2 - Upgrade to Gutsy and use the packaged KTorrent (2.2.1 I believe).  I have been using this one for a few weeks now without any problems.

For all the trouble that Gutsy is causing many people right now, I would stick with Feisty and install the official version from the website.  Maybe in a few weeks/months the major bugs in Gutsy will be worked out.  Hope this helps.

---

### Post by sonofusion82 on 2007-10-28
also, if you do not want to ugrade as suggested by grantk86, 
ktorrents has some problems with DHT. try disabling DHT... ktorrent seems more stable without DHT

---

### Post by Dr. Cox on 2007-10-30
have the same problem. my OS is ubuntu 7.10. overnight, my deluge icon disappears. i 'm perfectly able to restart it, however, it rechecks every torrent, which takes ages. also, it's time wasted.

what can be wrong, why does DELUGE stop working after some period of time?

---

