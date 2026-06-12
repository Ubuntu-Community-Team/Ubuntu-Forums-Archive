---
title: "Discover displays &quot;Failed to obtain Authentication&quot; when trying to open it from app m"
date: 2021-06-04
forum: General Help
---

### Post by deputy on 2021-06-04
I have setup Lubuntu (Ubuntu 21.04) on my box. I setup an SSH tunnel to connect to it using VNC on my windows laptop and I can successfully login using my VNC viewer. I started installing some applications using the Discover app in the Applications->System menu. No problems whatsoever. I wanted to install the Telegram desktop client, but instead of using the Discover app I installed it using terminal with "sudo snap install telegram-desktop" which was successful. Now each time I open Discover using the Applications menu it displays "Failed to obtain Authentication" and I can't install any app through it. Have no problem installing packages through the command line but Discover seems to have lost permissions.

[IMG]https://imgur.com/a/DN1PyHH[/IMG]

I tried looking at another post with this problem but it doesn't apply to my case. I still haven't been able to resolve this.[ATTACH=CONFIG]288611[/ATTACH]

---

### Post by guiverc on 2021-06-05
I have no experience with this issue sorry.

I noted on [https://forum.kde.org/viewtopic.php?f=225&t=169159](https://forum.kde.org/viewtopic.php?f=225&t=169159) that a few users have reported issue with `chrome-remote-desktop` package causing this issue.  Maybe worth a look/explore (do you have it installed?)

---

