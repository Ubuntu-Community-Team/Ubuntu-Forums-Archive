---
title: "No options when logging in."
date: 2014-06-20
forum: General Help
---

### Post by Renholder57 on 2014-06-20
Hello

I've installed the GNOME shell, but I'm not seeing the option to choose it when I log in. I'm not even seeing the icon that's usually there to choose other options. Is there something else I need to enable?

[IMG]http://imgur.com/znGrPyx.jpg[/IMG]

---

### Post by xc3RnbFO8P on 2014-06-20
Try this:
> sudo apt-get install --reinstall linux-image-$(uname -r) 
and restart

---

### Post by Renholder57 on 2014-06-20
Thanks for the help but that didn't help.

---

### Post by kansasnoob on 2014-06-20
Please open a terminal and post the output of:

```
apt-cache policy gnome-session*
```

---

### Post by kansasnoob on 2014-06-21
Where I was headed with that is this bug:

[https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1284417](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1284417)

Looks like no one else is going to do the SRU request so I guess I'll try, but it'll be my first :-k

Anyway you probably just need to:

```
sudo apt-get install gnome-session
```

And if you want the new GNOME Classic also:

```
sudo apt-get install gnome-shell-extensions
```

That also provides some useful extensions that can be applied in the standard gnome-shell session using GNOME Tweak if desired.

Or if you want to go totally retro:

[http://ubuntuforums.org/showthread.php?t=2220264](http://ubuntuforums.org/showthread.php?t=2220264)

---

### Post by Renholder57 on 2014-06-24
> **kansasnoob said:**
> Where I was headed with that is this bug:

[https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1284417](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1284417)

Looks like no one else is going to do the SRU request so I guess I'll try, but it'll be my first :-k

Anyway you probably just need to:

```
sudo apt-get install gnome-session
```

And if you want the new GNOME Classic also:

```
sudo apt-get install gnome-shell-extensions
```

That also provides some useful extensions that can be applied in the standard gnome-shell session using GNOME Tweak if desired.

Or if you want to go totally retro:

[http://ubuntuforums.org/showthread.php?t=2220264](http://ubuntuforums.org/showthread.php?t=2220264)


That worked! Thanks a bunch.

---

