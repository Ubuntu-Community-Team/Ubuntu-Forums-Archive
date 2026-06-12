---
title: "X Server Won't Start"
date: 2007-08-14
forum: General Help
---

### Post by newyearsproject on 2007-08-14
I am a new Ubuntu user and I think I bit off a little bit more than I can chew.  Although I am tech-savvy, I seem to have gotten myself into a bit of a pickle.

I can't get X to start.

I was upgrading from Dapper to Edgy, while at the same time trying to install the xgl visual package...I know...like I said, I bit off more than I should have been chewing.  Now whenever it loads up, it won't initiate the screen.  I'll communicate as much of the error report as possible, as I am writing this from another machine and can't access anything except nano on my ubuntu machine.

error opening security policy file /etc/X11/xserver/SecurityPolicy
(EE) xf86OpenSerial: Cannot open device /dev/wacom
     No such file or directory.
Error opening /dev/wacom : No such file or directory
...the last 3 lines repeat about 5 more times...

Fatal server error:
could not open default font 'fixed'

I've searched all over the place and have tried lots of editing of xorg.conf, but nothing seems to work.  Anything you can offer up as help will be greatly appreciated!!

Thank you!

---

### Post by apetresc on 2007-08-14
Could you post the contents of your xorg.conf file?

As a general rule, whenever you have an Xorg-related problem, it's a good idea to post that file since  X problems are simply configuration problems 99% of the time.

---

