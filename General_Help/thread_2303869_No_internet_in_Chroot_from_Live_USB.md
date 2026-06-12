---
title: "No internet in Chroot from Live USB"
date: 2015-11-22
forum: General Help
---

### Post by childintime on 2015-11-22
So long story short, I got a kernel panic message when booting Ubuntu 14.04 and I am not be able to boot with any of the available kernels, nor to recovery mode.

What I am trying to do it update kernel from Live usb using chroot. I am using a guide like one of these:

1. [http://askubuntu.com/questions/28099/how-to-restore-a-system-after-accidentally-removing-all-kernels](http://askubuntu.com/questions/28099/how-to-restore-a-system-after-accidentally-removing-all-kernels)
2. [http://aaronbonner.io/post/21103731114/chroot-into-a-broken-linux-install](http://aaronbonner.io/post/21103731114/chroot-into-a-broken-linux-install)

And everything goes well but I can't seem to have internet in my chroot. I copy the /etc/resolv.conf file as they mention but when I use apt-get update I get bunch of "cannot resolve" messages.

I have internet in my live usb environment though, so what can be the issue?

---

