---
title: "change notifications"
date: 2016-07-12
forum: General Help
---

### Post by jer333 on 2016-07-12
ok so when I had an xfce based distro it had really nice notifications. If I wanted to dismiss them I clicked them. now I got this ubuntu unity and the notifications just dim but stay in the way if my mouse goes there. it is terribly annoying. they get in the way of my work and my only choice is to wait for them to go away when they sit themselves right in the way of my work. :mad: Is there any other way to get these STUPID notifications to act right?! maybe there is some wierd notification plugin thing that I can uninstall and get some xfce notifier that is fit for an actual operating system! thanks!

---

### Post by vasa1 on 2016-07-13
The solution probably involves installing **xfce4-notifyd** which is the notification system used by Xubuntu (and Lubuntu).

---

### Post by jer333 on 2016-07-13
oh wow ok. but then wouldnt I have to turn of the default? how do I do that?

---

### Post by vasa1 on 2016-07-13
See [http://askubuntu.com/questions/49796/replace-notifyosd-with-the-xfce-version](http://askubuntu.com/questions/49796/replace-notifyosd-with-the-xfce-version) though it's from 2011.

---

### Post by jer333 on 2016-07-13
cool so it automatically kicks the horrible kids, that's nice. thanks for your help @vassa1 will install!

---

### Post by vasa1 on 2016-07-13
You could play safe and use _-s_ to simulate what will be installed (and removed as a consequence).

So, in this case, you'd first run
```
apt-get install -s xfce4-notifyd
``` without any need for sudo and then, if you want to actually proceed, run```
sudo apt-get install xfce4-notifyd
```

---

### Post by jer333 on 2016-07-13
ok just installed now I'm going to try to emulate a notificationalsimeitiousness ;)


oh darn. I send myself an email with a different email address and it does not show any notification >:C


ok nvm last post I tried inserting drive and ejecting it and I got a notification but for pete's sake the same old unity notification showed!


now I'm really perplexed. I tried even running 'apt remove notify-osd' and I still got those stupid unity notifications... what's going on?


SO MY COMPUTER JUST SAID IT HAD AN INTERNAL ERROR THEN REFUSED TO CONNECT TO THE INTERNET!!! EVEN AFTER 2 RESTARTS. WILL NOT CONNECT TO MY WIFI AT ALL!!!!! I guess that's it for UBUNTU. probably going to install Linux Mint or Chalet OS

---

### Post by QIII on 2016-07-13
OK.  Thanks for shouting.

Best wishes to you.

---

