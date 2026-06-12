---
title: "update has caused problems with Java"
date: 2013-02-02
forum: General Help
---

### Post by jockyburns on 2013-02-02
I did a regular update of my system (12.04) yesterday . I usually update when the update manager tells me to do so (and that's what I did )  Usually don't take any notice of what it wants to update as it's always worked before. Yesterday it updated and since then various sites have been unable to load plugins. Facebook and Youtube sites all throw up a "couldn't load plugin" message
This is my version of java
> java version "1.7.0_11"
Java(TM) SE Runtime Environment (build 1.7.0_11-b21)
Java HotSpot(TM) Client VM (build 23.6-b04, mixed mode)

I did notice yesterday, whilst updating , there was something relating to java in the update. 
Any help guys ??

---

### Post by Laobi on 2013-02-02
You can check what was updated by looking at this log file:
/var/log/apt/history.log

---

### Post by jockyburns on 2013-02-02
Just had a look in there and here's the result
> Start-Date: 2013-02-01  17:48:18
Commandline: aptdaemon role='role-commit-packages' sender=':1.67'
Install: linux-headers-3.2.0-37:i386 (3.2.0-37.58), linux-headers-3.2.0-37-generic-pae:i386 (3.2.0-37.58), linux-image-3.2.0-37-generic-pae:i386 (3.2.0-37.58)
Upgrade: libtelepathy-glib0:i386 (0.18.0-1ubuntu1, 0.18.2-0ubuntu1), oracle-java7-installer:i386 (7u11-0~webupd8~0, 7u11-0~webupd8~3), linux-image-generic-pae:i386 (3.2.0.36.43, 3.2.0.37.44), initramfs-tools-bin:i386 (0.99ubuntu13, 0.99ubuntu13.1), linux-libc-dev:i386 (3.2.0-36.57, 3.2.0-37.58), initramfs-tools:i386 (0.99ubuntu13, 0.99ubuntu13.1), jockey-common:i386 (0.9.7-0ubuntu7.4, 0.9.7-0ubuntu7.7), linux-generic-pae:i386 (3.2.0.36.43, 3.2.0.37.44), jockey-gtk:i386 (0.9.7-0ubuntu7.4, 0.9.7-0ubuntu7.7), google-chrome-stable:i386 (24.0.1312.56-r177594, 24.0.1312.57-r178923), linux-headers-generic-pae:i386 (3.2.0.36.43, 3.2.0.37.44)
End-Date: 2013-02-01  17:51:19

Have checked that java is working on the java test page, but will only work after I have selected the "Allow plugin to run on this site" message at the top of the Chrome browser (this can't be right as it should run on all sites. 
On Facebook I tried to run some games and it says "couldn't start plugin" When I open the java console of the web browser, theres some interesting results.
> Unsafe JavaScript attempt to access frame with URL [http://bubble.6waves.com/web/?fb_source=bookmark_apps&ref=bookmarks&count=0&fb_bmpos=8_0](http://bubble.6waves.com/web/?fb_source=bookmark_apps&ref=bookmarks&count=0&fb_bmpos=8_0) from frame with URL [https://s-static.ak.facebook.com/connect/xd_arbiter.php?version=18#channel=…com&channel_path=%2Fchannel.html%3Ffb_xd_fragment%23xd_sig%3Df240b537f4%26](https://s-static.ak.facebook.com/connect/xd_arbiter.php?version=18#channel=…com&channel_path=%2Fchannel.html%3Ffb_xd_fragment%23xd_sig%3Df240b537f4%26). The frame requesting access has a protocol of 'https', the frame being accessed has a protocol of 'http'. Protocols must match.
So it does seem to be something broken with Java, somewhere along the line. For now I'm stumped completely and it's destroying my initial surge of confidence with Ubuntu, to the extent, I will have to consider the dreaded alternatives of a Win7 install

---

### Post by QIII on 2013-02-02
Don't throw the baby out with the bath water.

[http://askubuntu.com/questions/250448/youtube-couldnt-load-plug-in](http://askubuntu.com/questions/250448/youtube-couldnt-load-plug-in)

may be what you are looking for.

JavaScript is NOT Java.  The two have nothing to do with each other except for a historical happenstance in naming.  That warning does not mean there is something wrong with what you have installed on your machine, but in the way the web page is constructed.

What happens if you use Firefox?

---

### Post by jockyburns on 2013-02-02
I have tried using both Chrome (my preferred browser) and Mozilla Firefox. Firefox will load, but is extremely jittery. Gameplay is jerky at best and almost impossible at worst, although video seems fine, if slightly slow at loading . So could be a problem with Chrome?, but Chrome hasn't had any updates.

---

### Post by jockyburns on 2013-02-02
Thankyou QIII. I followed your link and have disabled the pepper flash plugin and all is well again. Strange though that this would happen. Do people test such things before releasing updates? (or just release and be damned) ?

---

### Post by QIII on 2013-02-02
Although it happens only once in a blue moon, we software developers do, from time to time, fail to be god-like in our powers and we make human mistakes...

---

### Post by raja.genupula on 2013-02-02
> **jockyburns said:**
> Thankyou QIII. I followed your link and have disabled the pepper flash plugin and all is well again. Strange though that this would happen. Do people test such things before releasing updates? (or just release and be damned) ?

well QIII is really nice with Java and once again proved :D.

@OP No , before releasing the updates for stable version , they will test on many Computers/Hardware for fixing all upcoming issues. This will made the Ubuntu as strong Enough and stable. but sometimes you know things will happen like this,but soon they will be fixed too. you can also participate by reporting them to launchpad.

---

