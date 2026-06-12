---
title: "Netflix on Ubuntu Pipelight working, but going into standby."
date: 2016-09-19
forum: General Help
---

### Post by Anders_Hjlund on 2016-09-19
Hi,

I have Pipelight, User Agent Overrider working and can perfectly watch movies. My only issue is that my computer goes into standby every 10 minute, I have updated my power settings (please find screenshot) but the issue is still occurring.

[ATTACH=CONFIG]271263[/ATTACH]

This is my ```
lsb_release -a
LSB Version:    core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch:core-4.1-amd64:core-4.1-noarch:security-4.0-amd64:security-4.0-noarch:security-4.1-amd64:security-4.1-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial

```

Anyone who can help me resolve my problem? Thank you for your time and effort. Anders

---

### Post by #&amp;thj^% on 2016-09-19
Caffeine is a package very important cause inhibits the screen for 
playing videos on the web browsers. Actually is offered on the main 
repository of Ubuntu 16.04 but disabled by default. I think that 
Caffeine It should be enabled by default.
> Caffeine is a tool used to temporarily  prevent the activation of the screensaver / lock screen / sleep mode,  when using full-screen windows. The application is useful if you're  using a video player that doesn't do this automatically, when listening  to music, etc.

More Info for caffeine: [http://www.webupd8.org/2016/04/things-to-do-after-installing-ubuntu-1604-lts-xenial-xerus.html](http://www.webupd8.org/2016/04/things-to-do-after-installing-ubuntu-1604-lts-xenial-xerus.html)
```
sudo apt install caffeine
```
And remember it is not on by default and you should find it in your panel after launching it.
Hope this is useful.

---

### Post by deadflowr on 2016-09-19
Check the timeout setting (Turn off screen when inactive for: ) in Brightness and Lock.

---

### Post by #&amp;thj^% on 2016-09-19
> **deadflowr said:**
> Check the timeout setting (Turn off screen when inactive for: ) in Brightness and Lock.

+1:) But i found that setting usually was set to 30 mins to off was default...his is going every 10 mins.
But worth a look.

---

### Post by deadflowr on 2016-09-19
I guess we're both wrong.
the default screensaver timeout now is only 5 minutes.

---

### Post by Anders_Hjlund on 2016-09-19
Thank you both! I believe you might both be right.

I have installed Caffeine, I found the lock setting on the default 5 minutes. But I will prefer my caffeine setup.

Thank you so much for your great help!

---

### Post by #&amp;thj^% on 2016-09-19
Great good to hear....and we just love our deadflowr around here...She is a keeper.

---

