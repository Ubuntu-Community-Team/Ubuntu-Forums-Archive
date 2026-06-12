---
title: "Synaptics won't let me lock down versions"
date: 2006-11-30
forum: General Help
---

### Post by penguinmaster on 2006-11-30
I was trying to downgrade FireFox back to 1.5, because I'm not a huge fan 2.0.  I really hate that you can only open like 10 tabs before you have to scroll.  I followed directions to downgrade and when I tried to the version, Synaptics just goes to a blank screen and doesn't lock the version.  I tried to lock the versions of other programs just to see if it works, and they don't.  

Anybody have any thoughts?

---

### Post by penguinmaster on 2006-11-30
shameless bump

---

### Post by taurus on 2006-11-30
What if you just remove firefox 2.0 first and then install 1.5 after that!!!

---

### Post by penguinmaster on 2006-11-30
I have done that, that's what brought this to my attention.  I followed the how to on here on how to remove firefox 2.0.  Then I changed my sources to dapper sources, reintalled firefox.  Tried to lock version 1.5 which it wouldn't do.  Then I reinstated my edgy source list and it always wants to upgrade.  Another odd thing is when you try to completely remove firefox 2.0 it forces me to remove the ubuntu-desktop package.  I'm not sure what's up.  Also that does not solve my problem of not being able to lock down anything in synaptics.

---

### Post by penguinmaster on 2006-11-30
yet another shameless bump...someone has to know!

---

### Post by citizenr on 2006-12-01
yes, locking is broken, I had a wine that I really wanted to stay 2 versions back and couldnt lock it, now its libsdl (current repo libsdl is BROKEN, was broken for 2 months and devs seem to not care about it) and I cant even lock my local patched copies :/

[https://bugs.launchpad.net/distros/ubuntu/+source/synaptic/+bug/67146](https://bugs.launchpad.net/distros/ubuntu/+source/synaptic/+bug/67146)

---

### Post by NobodySpecial on 2006-12-26
A temporary fix is available.

Set preferences manually:
```
sudo gedit /etc/apt/preferences
```

This is what I did for mplayer & ffmpeg after compiling via SVN:
```
Package: ffmpeg
Pin: version 20061226-Edgy-1
Pin-Priority: 1000
Package: mplayer
Pin: version 20061226-Edgy-1
Pin-Priority: 1000

```

Of course, replace the versions with yours as described by Synaptic.

---

