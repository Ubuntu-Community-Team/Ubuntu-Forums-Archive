---
title: "Nvidia doesn't appear in Hardware Drivers [with workaround]"
date: 2008-05-16
forum: General Help
---

### Post by decoherence on 2008-05-16
I tried to get the proprietary nvidia driver working, however when I went to Hardware Drivers it gave me an empty list window and told me "No Restriced Drivers are in Use."

Well yeah. I know that. That's the problem! :confused:

Anyway, you can get nvidia going the (new) 'old fashioned' way. First, make sure you have the appropriate nvidia package installed. I'm using nvidia-glx-new. 

Drop to a console by typing Ctrl Alt F1 and log in (your password is not echoed back to you.) These commands need to be run as root, so either preface each one with sudo or use 'sudo -s' to run a root shell.

```
/etc/init.d/gdm stop
X -configure
X -config /home/USERNAME/xorg.conf.new 
```that last command was to make sure X detected things properly -- if you get a cursor, it worked. get out of it with Ctrl Alt Backspace. If it didn't work, your problem likely won't be solved here. Oh and of course replace USERNAME with your user name ... moving on
```
mv /home/USERNAME/xorg.conf.new /etc/X11/xorg.conf
nvidia-xconfig
depmod
/etc/init.d/gdm start
```

That did it for me!

bug report
[https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/231069](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/231069)

---

