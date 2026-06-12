---
title: "Use Newton Desktop Wiki on Gutsy"
date: 2007-12-23
forum: General Help
---

### Post by tommie-lie on 2007-12-23
Hi folks,

Even though the Newton SVN tree does not exist anymore and the developer seems to have abandoned the project, I'm still using Newton and here is how you can make it work on Gutsy:

1. Add the "/usr/lib/firefox" to your /etc/ld.so.conf. After that, mine looks like this:
```
include /etc/ld.so.conf.d/*.conf

# make newton work
/usr/lib/firefox
```
After that, run ```
sudo ldconfig
```
This is the known workaround for previous Ubuntu releases.

2. Additionally, for Gutsy, add the following line to /etc/environment:
```
MOZILLA_FIVE_HOME=/usr/lib/firefox
```
Now you have to logout and login again (or reboot your machine) to make the changes take effect.

After that, you can use Newton in the convenient, well-known way from within the gnome-panel without having to start it manually.

According to the [Launchpad bug]("https://bugs.launchpad.net/firefox/+bug/26436/comments/54"), this issue will finally be fixed in xulrunner-1.9, which will be part of Hardy Heron.

---

### Post by K.Mandla on 2007-12-25
Moved to General Help.

---

### Post by [woodstock] on 2007-12-25
Thank you for that guide. I really like newton and I am glad that I can finally use it again.

---

