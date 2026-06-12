---
title: "Random applications open on start up"
date: 2013-12-07
forum: General Help
---

### Post by rdh61 on 2013-12-07
Hi,

Using the Xubuntu desktop (with xfce version 4.1) with a primary Lubuntu 12.10 installation, I have noticed that random applications open on start up. First it was Chromium and Thunar file manager, then they stopped and Synaptic kept opening (without administrator privileges), now that has stopped and it's Thunar again. Could these be applications I have recently used frequently and Xubuntu thinks I'll want to run them again? Well, I'd rather decide myself. How can I change this behaviour?

Many thanks.

---

### Post by claracc on 2013-12-07
In my ubuntu 12.04, I can click on menu: apps -->system tools ---> preferences ---> apps at starting and there, I can tick or untick the apps I want to run at the beginning, also you can add or remove other apps

---

### Post by amanchesterman on 2013-12-07
I have Xubuntu 12.10, the procedure is slightly different:
- click on Settings Manager > Session and Startup (under the System heading), then the Session tab
- this lists all the applications currently running in my session, and at the right there is a column headed 'restart style'
- click on the applications you **don't** want to restart automatically and change the 'restart style' value to 'if running'
- make sure that you close those applications before you shut down or restart

---

### Post by rdh61 on 2013-12-07
Thank you to both. Yes, amanchesterman, the procedure should be as you describe. However, the application that currently opens automatically is Thunar, it is marked "if running", and I have always been careful to close it before shutting down. Yet it does not behave as it should, and opens anyway on start up.

Also in "Session and Startup", there is an "Application Autostart" tab. Thunar is not listed in it.

Any other suggestions?

---

### Post by vasa1 on 2013-12-07
Maybe it has something to do with your "session cache".
See [http://docs.xfce.org/xfce/xfce4-session/preferences](http://docs.xfce.org/xfce/xfce4-session/preferences)
and 
[http://askubuntu.com/q/382331/25656](http://askubuntu.com/q/382331/25656)
and
[http://ubuntuforums.org/showthread.php?t=2191629&p=12864536#post12864536](http://ubuntuforums.org/showthread.php?t=2191629&p=12864536#post12864536)

Re. the last link, I always log out via the first route.

---

### Post by rdh61 on 2013-12-09
Thank you vasa1, yes you are right, that does seem to be the problem. I guess I'll just have to be careful about the way I shut down the computer.

---

### Post by claracc on 2013-12-09
If you have fixed your problem, please mark the thread as solved with "thread tools" in order other posters can find information easily-

Thanks.

---

### Post by monkeybrain20122 on 2013-12-09
This is a very annoying problem of xfce for as long as I can remember. The only sure fire way to fix it, it seems, is to lock the session-cache. Right click it, set permission to  'none' and this would solve your problem once and for all. (deleting the cache doesn't solve the problem as it regenerates itself and I don't want to be always careful keeping track of how I log out or shut down)

---

### Post by rdh61 on 2013-12-09
Very good, monkeybrain20122! I've done what you suggested. 

@ claracc: yes I will, but I'll see how I go on the next few start ups, first.

---

