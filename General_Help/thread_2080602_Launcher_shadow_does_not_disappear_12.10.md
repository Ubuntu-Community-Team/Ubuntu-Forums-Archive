---
title: "Launcher shadow does not disappear 12.10"
date: 2012-11-04
forum: General Help
---

### Post by gsarrica on 2012-11-04
After updating to 12.10 I am noticing the shadow for the Launcher does not disappear. 

I have attached two example screenshots.

I have a Nvidia Geforce 660ti

I have tried both of the proprietary drivers without success. (nvidia-current and nvidia-experimental) 

Looks like this person is having the same issue.
[http://askubuntu.com/questions/204962/unity-launcher-autohide-leaves-ghost-behind](http://askubuntu.com/questions/204962/unity-launcher-autohide-leaves-ghost-behind)

Any ideas on how to solve this? Or where I can file a bug report?

Thanks in advance!

---

### Post by José Serra on 2012-11-27
In a terminal execute ```
xrandr
``` and see if you get this error: failed to get size of gamma for output default 

I got the same problem if I use xorg.conf.failsafe settings.

---

### Post by gsarrica on 2012-11-27
An update must have fixed this. Thanks anyway.

---

