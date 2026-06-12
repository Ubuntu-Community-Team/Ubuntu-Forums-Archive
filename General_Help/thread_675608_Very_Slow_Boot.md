---
title: "Very Slow Boot"
date: 2008-01-22
forum: General Help
---

### Post by verycontrasty on 2008-01-22
Hi,

I've just installed Ubuntu 7.10 on my Toshiba Satellite Pro M50 with Intel Celeron 1.90GHz, 1.25GB RAM, and 40 GB HDD.

Apart from some initial problems overcoming the Atheros wireless drivers problem it has been great, except for one issue: it takes a couple of minutes to boot up.

I'm very new to Ubuntu and Linux in general so I've no idea if this is normal or it is something that can be corrected. Can anyone put my mind at ease or give me any suggestions on how to tackle this problem?

Thanks!!!

---

### Post by erfahren on 2008-01-22
you might be talking about the issue with usplash - you basically get a dark sceen with nothing until you reach the login sceen

see: [http://ubuntuforums.org/showthread.php?t=581075](http://ubuntuforums.org/showthread.php?t=581075)

---

### Post by erfahren on 2008-01-22
oh, sorry - maybe I should include this (I was thinking that thread had more info than it did) - if that seems to be the problem you're having then open up the terminal - Apps > Accessories > Terminal

to open the file up with admin (root) permissions in the text editor (Gedit) - enter:
```

gksudo gedit /etc/usplash.conf

```
and edit it for your resolutions and save

then update the theme like it says - enter:
```

sudo update-usplash-theme usplash-theme-ubuntu

```
reboot and see if it helps

---

### Post by verycontrasty on 2008-01-24
Thanks, I'll give it a try and get back to you.

---

