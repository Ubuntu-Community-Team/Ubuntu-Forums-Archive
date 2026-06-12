---
title: "Website says, &quot;get the lastest flash player&quot;, and I have 11.2 installed."
date: 2013-04-11
forum: General Help
---

### Post by ant2ne on 2013-04-11
One of my favorite websites must have upgraded beyond 11.2 just today. Yesterday it worked just fine.I now get the message "get the lastest flash player" & "The Adobe Flash Player is required for video playback." in front of where I should be viewing video.
```
ant2ne@ant2nestation:~$ dpkg -l | grep flash
ii  flashplugin-installer                  11.2.202.280ubuntu0.12.04.1                          Adobe Flash Player plugin installer
ant2ne@ant2nestation:~$ 

```
Anybody know of any work arounds? I know html 5 is coming. But it isn't here yet.

---

### Post by ant2ne on 2013-04-11
OMG that worked. I saw "get the latest" and then I saw ```
NOTE: Adobe Flash Player 11.2 will be the last version to target Linux as a supported platform. Adobe will continue to provide security backports to Flash Player 11.2 for Linux.
``` and I panicked.

Thanks

---

