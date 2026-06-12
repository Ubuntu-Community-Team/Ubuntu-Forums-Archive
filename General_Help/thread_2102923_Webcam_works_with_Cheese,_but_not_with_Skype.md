---
title: "Webcam works with Cheese, but not with Skype"
date: 2013-01-08
forum: General Help
---

### Post by gwu777 on 2013-01-08
Hi there,

Same old, same old.  I am trying to have the webcam working with skype. As many of you it is working with cheese but in skype I have a black screen. It is a microsoft HD Webcam.

Skype is Skype-ubuntu-precise_4.1.0.20-1_i386.deb
I have ubuntu 64 12.10. THe webcam is a microsoft HD, it was working on 12.04.

I have done all the usual suspect, I have start skype with all the following:
> LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype

> LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l2convert.so skype

> sh -c 'LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype "$@"'

> sh -c 'LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l2convert.so skype "$@"'


> locate v4l1compat.so

returns
> /usr/lib/i386-linux-gnu/libv4l/v4l1compat.so
/usr/lib/x86_64-linux-gnu/libv4l/v4l1compat.so

Yet despite all of this, everytime I restart skype and go into option, the webcam led lights up for 3 or 4 seconds, but the screen stay black, any idea would be welcome.

Cheers.

---

### Post by xc3RnbFO8P on 2013-01-08
I think it is a bug in 12.10

---

### Post by gwu777 on 2013-01-08
> **Ringi said:**
> I think it is a bug in 12.10

Gosh am I glad to know it! Altough it will explain why I am scrapping my head for the last 2 hours on this problem, there must be a solution?!?!

---

### Post by xc3RnbFO8P on 2013-01-08
> **gwu777 said:**
> Gosh am I glad to know it! Altough it will explain why I am scrapping my head for the last 2 hours on this problem, there must be a solution?!?!
It takes ca. 2 hour to install 12.04 ;)

---

### Post by gwu777 on 2013-01-09
Do not want to be rude or anything, but this does not really help my case, it takes me more than 2 hours to setup my system as I like it, and I have just finished preparing it with 12.10. Not willing to start again!

Anyone has any helpfull information, it would be greatly appreciated.

---

### Post by xc3RnbFO8P on 2013-01-09
You are not rude,
you can report a bug here:
[https://bugs.launchpad.net/ubuntu/+source/skype/+bug/754162]("https://bugs.launchpad.net/ubuntu/+source/skype/+bug/754162")

---

