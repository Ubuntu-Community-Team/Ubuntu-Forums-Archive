---
title: "Suspend doesn't work after linux kernel upgrade..."
date: 2013-08-31
forum: General Help
---

### Post by vvozar on 2013-08-31
Hello all,

As title says: suspend option on my Ubuntu 12.04 stopped working properly after i have upgraded linux kernel (to Kernel Linux 3.10.10-031010-generic).

Full story:
I have a habit of rather using suspend option than to shutdown or hibernate Ubuntu (obviously, because of fast launching afterwards). Two days ago I accepted updating Google Chrome, and that's when my troubles started. Firstly, this new version of Google Chrome started freezing and crashing. But, suspend was still working fine then. I have googled around, and found some posts that updating linux kernel could help. I did that, following this instructions: [http://linuxg.net/how-to-install-kernel-3-10-on-ubuntu-linux-mint-debian-and-derivates/](http://linuxg.net/how-to-install-kernel-3-10-on-ubuntu-linux-mint-debian-and-derivates/) . Upgrading past flawless, but suspend is no longer working. Actually Ubuntu does go to suspend mode, but it won't come back. When i press any button to invoke coming back from suspend mode, laptop lights does turn on, fan turns on, but display does't come up, not even a backlight, just black screen.
I have searched on this issue, and found this thread : [http://ubuntuforums.org/showthread.php?p=11926504](http://ubuntuforums.org/showthread.php?p=11926504) , but those scripts doesn't worked for me. Then, i tried loading Ubuntu with previous kernel version, but didn't help.
Hibernate is working OK ("pm-hibernate" - command). 
One another thing i noticed is that icons on sidebar dock look little different then previously (like they are little more highlighted). Also, when starting Ubuntu, for a second, screen goes light grey, and then (probably) when driver loads, screen background image and icons come up (just want to say that screen wasn't going grey before).

All this looks like some issue with graphics. Or maybe something else???
Any ideas, suggestions, help are appreciated.

---

### Post by vvozar on 2013-09-01
[SOLVED] Issue was about graphics drivers. I have returned to using open source Radeon drivers, because proprietary "fglrx" driver is not working properly. I tried also with fresh install of "fglrx" [FONT=Ubuntu Mono]driver following this tutorial : [/FONT][https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI), but didn't help. Then I have purged fglrx drivers : [https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection#Problem:_Need_to_purge_-fglrx](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection#Problem:_Need_to_purge_-fglrx) , and all is fine.

---

