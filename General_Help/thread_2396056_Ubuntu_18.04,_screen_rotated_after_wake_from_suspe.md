---
title: "Ubuntu 18.04, screen rotated after wake from suspend"
date: 2018-07-10
forum: General Help
---

### Post by brotakul on 2018-07-10
Hi,
I just installed Ubuntu 18.04 and after i wake up my laptop from suspend, the display is always rotated to left (both logon screen and desktop after login).
I searched the web for solutions and i found some other guys having the same issue on multiple versions (e.g. 18.04, 17.10). The solutions were the following, i tried them but none actually worked:
- disable the accelerometer module (blacklist lis3lv02d in /etc/modprobe.d/blacklist.conf)
- disable iio-sensor-proxy.service

"xrandr --output eDP-1 --rotate normal" works until next wake, but it's not a solution per se. Any other people having this issue? Maybe you can help... Thanks!
PS: i'm a linux noob, if you have any ideea to solve this, please try explain it in detail :)

---

### Post by emackey3k on 2019-05-04
I am also having the same issue.  Also tried removing iio-sensor-proxy.service.  I'm on a HP Elitebook.

---

