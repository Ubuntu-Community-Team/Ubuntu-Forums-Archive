---
title: "Firefox question"
date: 2007-12-08
forum: General Help
---

### Post by herbster on 2007-12-08
I uninstalled Firefox from repos and downloaded the tar off mozilla.com, and now I have a firefox folder on my desktop, so where do I put it? In /usr/local or /usr/bin or something? I'd like to put it somewhere and have "firefox" run from the terminal as before, if that is possible.

---

### Post by CalonDdraig on 2007-12-08
I'd put the firefox binary in /usr/bin/ if I were you. It's probably best to install it from a repository though so its files go in all the right places... you can still run it from a terminal though if you do. If you run the command "apt-get install firefox" from a terminal or use Synaptic to get and install the file from a repository, you can still run firefox as follows: 

:~$./firefox

Or 

:~$./usr/bin/firefox

Hope this helps:)

CalonDdraig

---

### Post by CalonDdraig on 2007-12-08
Sorry for my above reply, I've just noticed that you uninstalled from repos. 

If I were you, I'd just have the folder in /home/*yourname*/firefox/ or something like that... that way you can run from userland as follows: 

:~$./home/*whatever*/firefox/firefox

That'd be my advice for funning FF in userland:)

~CalonDdraig

---

### Post by aysiu on 2007-12-08
This should help you:
[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

---

### Post by herbster on 2007-12-08
> **aysiu said:**
> This should help you:
[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

Thanks a lot aysiu, it was the links that was fudging it up for me, that worked :)

---

