---
title: "Cannot install ATI drivers"
date: 2008-06-25
forum: General Help
---

### Post by Lord Xeb on 2008-06-25
When I tried to install the ATI drivers on my brother's laptop, it mucks up everything and it will go into safe graphics mode from which I cannot get out. It says the drivers where installed successfully but then when I reboot they do not work. The drivers do not show up in restricted drivers manager nor do I see them when use 'fglrxinfo'. It recognizes his graphics card as a Mobility Radeon FireGL 9000... Are there any drivers for that? I have tried all 3 of the different drives and none of them work. Even after removing all the the ATI drivers and setting it back the default driver (which is generic) it still stays in safe graphics mode. I have added his xorg.config file to this post.


Please help me. He would like to have the effects that I have but his computer does exactly want to cooperate (and it does like to cooperate even with windows. Rebuilding it is a nightmare ) I do not know if I have supplied enough information. Let me know what you need.

---

### Post by Lord Xeb on 2008-06-25
Can anyone do anything?

---

### Post by Lord Xeb on 2008-06-25
e_e real cool guys.

---

### Post by Rocket2DMn on 2008-06-25
That card does not use restricted drivers, it is too old - it requires the open source "ati" drivers.  You should remove the fglrx drivers.
```
sudo apt-get remove --purge xorg-driver-fglrx
sudo dpkg-reconfigure xserver-xorg -phigh
```
Or if you used EnvyNG, you can remove them from there.  If you installed them manually from ATI's website, you need to use the installer file to remove them.
Then restart X with CTRL+ALT+BACKSPACE or reboot the computer.
The "ati" drivers will get used automatically.  To enable Compiz, see here - [http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633)

---

### Post by Lord Xeb on 2008-06-25
Thank You!!!!!!!

---

