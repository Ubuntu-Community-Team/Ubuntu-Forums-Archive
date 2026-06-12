---
title: "Upgrade to 14.04 - Freeze after login"
date: 2014-04-23
forum: General Help
---

### Post by paul127 on 2014-04-23
Hi everybody,

This week, I upgraded my Ubuntu to the last version 14.04. I have a dual-boot Ubuntu/Windows 8.1 which works perfectly.
The new version worked fine a few times, but now, I choose Ubuntu, it launches, I enter my password, and then it freezes. I see the desktop picture but without the bar on the left, nor the bar on the top : only the image. I can move my mouse, and I have access to a terminal with CTRL + ALT + F... but nothing else.

I don't know where this problem comes from... I've searched on Google, tried some things, but didn't solve the problem. In fact, I didn't really find someone with exactly the same problem. I read some stuff about completely frozen screen and mouse/keyboard but didn't work... The last thing I did while ubuntu was working correctly, was trying to install OpenCV, but I don't think it is linked...

So, how can I get my Linux back ? :/

I hope you will be able to help me,
Ask me if you want details or anything because it becomes really annoying.

Thank you for your help.
Paul

---

### Post by thorekk on 2014-04-27
I have experienced the same problem. I am using an AMD machine. I've found the problem is coming from the fglrx driver, and the older kernel the system was using. Somehow during update the kernel stayed the older version.
I went to tty1 with ctrl+alt+f1 and logged in.
then did
```
sudo apt-get install linux-generic
sudo apt-get install --reinstall fglrx
```

then restart ubuntu
```

sudo shutdown -r now
```

Now login is working for me. Before this I have tried awful lot of other things, like dpkg-reconfigure of all packages and so on, so if it is not working for you I will write the other things I've tried also.

---

