---
title: "Key mapping problem after restart"
date: 2008-06-23
forum: General Help
---

### Post by ryanh on 2008-06-23
Hello all,

I am having a problem with my Ubuntu 8.04 installation with respect to keys doing strange things.

For example / turns into é and ? turns into É

If I go into the keyboard settings, and change the layout between any of the Generic 101,102,104,105 key layouts the keyboard works fine.

I'm using a plain old Microsoft Basic Keyboard 1.0A plugged into a PS2 port.


After I restart it shows the same keyboard layout, but the mapping goes all weird. Once I select another layout it works fine.
I'm using a standard USA layout as well.

Any help with this problem is greatly appreciated!


Thanks,
Ryan

---

### Post by tamoneya on 2008-06-23
use xkeycaps to remap the keys:```
sudo apt-get update
sudo apt-get install xkeycaps
xkeycaps
```

---

### Post by iaculallad on 2008-06-23
You could also try to reconfigure your xorg file for your keyboard problem:

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by ryanh on 2008-06-23
Thanks for the help guys, I couldn't find my keyboard using the xkeycaps program (when I chose one the key pressed never corresponded with the onscreen keyboard, 99% sure this was something I did wrong though, this program seems to have just about every layout under the sun!)

Reconfiguring xorg seems to work great. They take you through things step by step and provide suggestions along the way.

---

