---
title: "Filesystem image is now mounted in a new location. Previous location is now taken."
date: 2018-12-16
forum: General Help
---

### Post by Joseph_Watts on 2018-12-16
I had a drive located at /dev/sdg1 that has been mounted as Extra Storage 2T. For some reason it is now mounting as Extra Storage 2T1 causing a bunch of issues with path-dependent programs. Under my /media/joey/ directory, even when /dev/sdg1 is unmounted, I am still seeing a directory named Extra Storage 2T. I'm not sure how to go about removing this mounting because it seems like it is coming off of my main hdd. (I currently have 457gb free in my main partition. Right clicking and viewing properties for it shows 457gb free) I've attached a couple of screenshots to hopefully help.

Thanks,
Joey

[https://i.imgur.com/hrn2hHo.png](https://i.imgur.com/hrn2hHo.png)
[https://i.imgur.com/e8QEQma.png](https://i.imgur.com/e8QEQma.png)
[https://i.imgur.com/I1UGhFk.png](https://i.imgur.com/I1UGhFk.png)
[https://i.imgur.com/7RP0A8D.png](https://i.imgur.com/7RP0A8D.png)

---

### Post by Joseph_Watts on 2018-12-16
It's been a long hour but I got it figured out.

I basically followed along with this post [https://ubuntuforums.org/showthread.php?t=2224142](https://ubuntuforums.org/showthread.php?t=2224142) and after rebooting I was suddenly able to remove all the directories inside, then remove the files themselves. This let me delete the folder named 'Extra Storage 2T'.

Thanks!

---

### Post by wildmanne39 on 2018-12-16
Please use the attachment facility by clicking on the paperclip or  use url's for images because apart from bandwidth issues for some, it makes it difficult for those using mobile devices to browse the forum.

Thanks for posting your solution!

---

