---
title: "Feisty won't start: X server error"
date: 2007-09-10
forum: General Help
---

### Post by JimNSB on 2007-09-10
I've been running 7.04 without any problems, but when I attempted to start the system up today I got a "*Failed to start the X Server*" error.  My video card is an nVidia 7600GT, using the Envy-installed driver.

After selecting **OK** on the blue/gray error screen I was dropped to a prompt, and saw this in the POST info:

> kinit: name_to_dev_t(/dev/disk/by-uuid/.....) = sda5(8,5)
kinit:trying to resume from /dev/disk/by-uuid/......
kinit: no resume image, doing normal boot
<login prompt>

Any suggestions on how I can fix this?  I researched it and found some posts involving ATI cards, but not nVidia ...so I figured I better ask before trying the solutions they contained.

thanks

---

### Post by sumguy231 on 2007-09-10
```
kinit: name_to_dev_t(/dev/disk/by-uuid/.....) = sda5(8,5)
kinit:trying to resume from /dev/disk/by-uuid/......
kinit: no resume image, doing normal boot
<login prompt>
```

I get that too, so it has nothing to do with your X server not working as mine works quite ok. I'm pretty sure that's completely normal. You can always run 
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` after logging in to reconfigure the X server into a working state. Also, if you want to find the error that led to the failure, you can look at /var/log/Xorg.log.0.

---

