---
title: "nxclient for windows + flash = crash"
date: 2007-07-14
forum: General Help
---

### Post by tigerstripedcat on 2007-07-14
For anyone using nomachine.  Could you try and reproduce my bug before I send it to the nomachine people.  Steps:

1) Start nx advanced server ("advanced" being the name of the deb I downloaded form their site
2) connect with nxclient from a *linux* machine open firefox or opera and go to a youtube.com video (any site with flash content)
3) disconnect session (NOT terminate) so the session is saved
4) Try and reconnect using a windows client

ERROR:
"The connect with the remote server was shut down.  Please check the state of your network connection"
and the session is no longer available to resume

Facts:
[LIST]
[*]This only happens using the windows client. In linux it's fine
[*]This has been tested with non flash content--works--with different browsers, opera and firefox--still crashes--with two different computers, winxp and 2003server--still crashes
[*]It seems necessary to start the browser from the linux client first.  if you start it in windows and then resume it doesn't crash
[/LIST]

There was a similar problem in an earlier version:
[http://mail.kde.org/pipermail/freenx-knx/2006-October/004224.html](http://mail.kde.org/pipermail/freenx-knx/2006-October/004224.html)
[http://www.nomachine.com/news-read.php?idnews=184](http://www.nomachine.com/news-read.php?idnews=184)

If anyone can verify this, so I know I'm not crazy, or just give me an idea of something to try, I would be happy to do so.  At the moment it's very frustrating to have my work vanish after working on it for hours.

THANKS!
TSC

---

