---
title: "no gui in ubuntu, revert back to previous card driver??"
date: 2008-04-20
forum: General Help
---

### Post by dryang on 2008-04-20
Hello,

I noticed the settings for my graphics card were set to : fglrx as the driver for my ati radeon mobile card. 

As i have been unable to use desktop effects i thought it might be a good idea to set (from the drop down menu) to ati radeon.

The computer asked for a re-start, now the computer re-boots to the command prompt. after entering my login/passwrd i'm left with the $.

I guess the machine doesn't like the new driver setting. How do i revert back to previous setting (fglrx). I DO NOT HAVE INTERNET CONNECTION, is this possible to restore?

HELP!!!

---

### Post by Happy_Man on 2008-04-20
It's quite simple. Once you get to the $, enter this line:

```
sudo nano /etc/X11/xorg.conf
```

and scroll down to the section labeled "Device"

There, you will see a line that looks like 

Driver:   radeon

or something similar. change the "radeon" to "fglrx" and then press ctrl-x, then y, then enter. After that, enter the line 
```
sudo /etc/init.d/gdm start
```

and hopefully, everything will work out.

---

