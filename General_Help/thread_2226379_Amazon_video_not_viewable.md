---
title: "Amazon video not viewable"
date: 2014-05-26
forum: General Help
---

### Post by meisen321 on 2014-05-26
I have recenlty updated to Ubuntu 13.10 and all seemed well. No problems to report.
I ordered an instant video from Amazon. I watched the trailer and it was viewable with no problems but when the video started and the flash player was being updated,for some reason, I was issued a message that the update failed and the video was not viewable. I thought that Canonical and Amazon were cooperating and that this would not be an issue.

---

### Post by monkeybrain20122 on 2014-05-26
Install hal [https://launchpad.net/~mjblenner/+archive/ppa-hal](https://launchpad.net/~mjblenner/+archive/ppa-hal)

---

### Post by meisen321 on 2014-05-27
THask you for responding . May I ask , exactly what is this install for and what is it supposed to do ?

---

### Post by monkeybrain20122 on 2014-05-28
It allows you to access drmed streaming contents with flash. Flash on Linux doesn't support drm.

[http://helpx.adobe.com/flash-player/kb/protected-video-content-play.html](http://helpx.adobe.com/flash-player/kb/protected-video-content-play.html)
Forget about the rest of the junks, just scroll to the bottom and do the test with and without hal. HAl (hardware abstraction layer) was in the repo in 12.04 but has been removed since 13.04 since it is deprecated, but there is no other way* to access drmed flash streams without hal, so this guy puts up a ppa for Ubuntu users.

* Well there is actually another way, install Windows flash with pipelight and switch between it and system flash, but that is quite recent.
[http://fds-team.de/cms/pipelight-installation.html](http://fds-team.de/cms/pipelight-installation.html)

---

### Post by Jan_Pearce on 2014-07-17
Thank you, installing hal worked for me.

---

