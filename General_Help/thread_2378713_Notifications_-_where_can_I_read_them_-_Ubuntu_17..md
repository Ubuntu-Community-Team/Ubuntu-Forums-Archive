---
title: "Notifications - where can I read them - Ubuntu 17.10"
date: 2017-11-26
forum: General Help
---

### Post by carusoswi on 2017-11-26
Running 17.10 and receiving notices when I sign in that I have notifications.  Where do I go do read them?
I have searched this forum, but didn't find an answer.
Advice appreciated.
Thanks.
Caruso

---

### Post by vasa1 on 2017-11-26
Will [https://launchpad.net/~jconti/+archive/ubuntu/recent-notifications?field.series_filter=artful](https://launchpad.net/~jconti/+archive/ubuntu/recent-notifications?field.series_filter=artful) help?

If that's not what you want, please go into more detail about "receiving notices when I sign in that I have notifications".

---

### Post by Dennis N on 2017-11-26
Open the calendar drop-down by clicking on the clock on the panel. A message area is on left side. Important messages (like notifying that updates are ready) seem to go there if they time out when they first pop up on desktop. I notice a little white dot by the clock when notifications are present.

---

### Post by carusoswi on 2017-11-26
Thanks for the replies.  I clicked on the clock, there was one notification about it being ok to unplug some windows something - not certain what.  To make my self as clear as possible, when I boot my computer or also when I am ready to enter my password after it goes to sleep, I see these messages that I have 1 notification or 4 notifications, etc.  I guess when I log on and don't open them, they must go away, because if they remained until read, I would probably have 50 of them by now.

Thanks for your help.

Caruso

---

### Post by vasa1 on 2017-11-26
If you don't have *inxi* installed, please install it from the software center or by using *apt-get*. If it isn't available you may need to enable the Universe repository first and then update your system). After that, run```
inxi -Fxz
```and post the output here. The output may help people understand more about your system and guide you better.

---

### Post by kkivi on 2017-12-03
Thank you!  I had the same problem

---

### Post by carusoswi on 2018-03-04
> **vasa1 said:**
> If you don't have *inxi* installed, please install it from the software center or by using *apt-get*. If it isn't available you may need to enable the Universe repository first and then update your system). After that, run```
inxi -Fxz
```and post the output here. The output may help people understand more about your system and guide you better.

Not finding that application in the software center, but, after reviewing this thread again, fell that pulling down the clock and checking the pane to the right is the answer to my question.  Thank to all for the replies.

Caruso

---

