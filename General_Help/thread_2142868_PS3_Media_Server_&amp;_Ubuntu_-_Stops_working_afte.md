---
title: "PS3 Media Server &amp; Ubuntu - Stops working after sleep"
date: 2013-05-07
forum: General Help
---

### Post by indigosunrise on 2013-05-07
Hey all,

Had a mild annoyance with PMS not working after computer goes to sleep and is awoken. In the PMS window it still displays tele and PS3 as detected renderers but isn't the case, and upon restarting the media server it detects no renderers.

Just wondering if anybody has had this problem as well and found a decent fix. It has occurred with all versions of PMS I have used with all versions of Ubuntu I have used, as well as Mint on my gfs computer.

Currently I'm running PMS 1.72.0 on Ubuntu 12.04, but as said I've had this problem over multiple distro versions with multiple versions of PMS. I even found a thread on these forums from a couple of years ago where somebody reported the same issue on 10.04 but there were no replies.
 
To get it up and running again restarting network-manager and then restarting PMS seems to fix it without needing to log out\in, but this is a pain currently since restarting that service in the GNOME 3 shell causes the DM to crash and freeze for a few minutes. 

If anybody can't offer a solution to this issue I guess I'll look into finding a way to automatically run commands upon awaking to terminate PMS, restart network-manager and then start PMS again which I'm sure is very doable after a google search but I'd prefer to tackle the bug head on by understanding why this problem occurs after sleep without fail and whether I can change some settings to rectify it.

Let me know if posting any outputs will help.

Cheers to all awesome participants of the Ubuntu Community, whether you can help or not.

---

### Post by indigosunrise on 2013-05-13
Well since nobody bothered to answer this one, just stumbled upon this script accidentally when doing a locate search for something:
/usr/lib/pm-utils/sleep.d/55NetworkManager

Have a feeling this is the cause of my problem.

If anybody down the track has the same issue, this would be where I'd start to look for a solution.

---

