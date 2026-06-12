---
title: "Firefox lost rights"
date: 2015-05-08
forum: General Help
---

### Post by AkAntA on 2015-05-08
Hi!
Not sure whether this supposed to be under General Help but I didn't come up with another place to put this in since my problem includes not one but at least two program in Ubuntu.

Briefly: When ever I open a link in Teamspeak 3 (opened with sudo), my user looses its rights to write to Firefox. Also if link is tried to open while Firefox is running it says "Firefox is already running, but is not responding. To open a new window, you must first close the existing Firefox process, or restart your system." so first I have to shut down the Firefox and then click the link.

First it seems to be all OK when the link is opened (Firefox shut down first), last session is restored and all the settings are as they should be, but when shutting that session down and starting a new session Firefox starts from the Ubuntu start page and all the settings are lost.

Luckily I found this thread [http://ubuntuforums.org/showthread.php?t=2204371](http://ubuntuforums.org/showthread.php?t=2204371) for my problem of lost session and settings, but now I have mapped this problem down to links in TS3. So now I'm able to avoid the problem but what would be the fix for this? I also think that any program ran under root that has this kind of chat system with web-links will cause same problem.

---

### Post by AkAntA on 2015-05-09
So I just realized why I'm losing those rights to root. It's because of sudo vs gksudo.

Yes.. I'm a newbie to Ubuntu but I'm trying hard to get a hang of it :lolflag:

---

