---
title: "Allowing autologin on startup of Lubuntu"
date: 2017-07-25
forum: General Help
---

### Post by jjhudak on 2017-07-25
When I installed lubuntu (V16-the current version) I opted NOT to have auto login...now that I am using it for awhile, I would like for it to autolog me in upon startup.

I looked and followed the guidance, here:[https://wiki.ubuntu.com/LightDM](https://wiki.ubuntu.com/LightDM)

Specifically:
make a file [B]/etc/lightdm/lightdm.conf.d/50-myconfig.conf

[/B]and added in it:

[Seat:*]
autologin-user=my_user_name
autologin-user-timeout=delay

I then saved the file, rebooted and got the Login prompt when it rebooted.
What am I doing wrong?  How to correct?
BTW, Lubuntu is operating as a guest OS under Virtual Box, and Windoz is the host OS.
Thanks
J

---

### Post by deadflowr on 2017-07-25
replace delay with a time
like
```
autologin-user-timeout=0
```
it runs in seconds.
any time should do.
(0 or 1 or 10)

---

### Post by jjhudak on 2017-07-25
thanks, good catch...if forgot to change it....I did set it to 0, unfortunately no joy.....

This is a stock lubuntu,  fully patched up until today....do I need anything else? 
J

---

