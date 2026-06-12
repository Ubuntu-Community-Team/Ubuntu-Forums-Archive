---
title: "video resolution"
date: 2007-01-30
forum: General Help
---

### Post by overules on 2007-01-30
hello.. i have an asus a8js laptop.. with a geforce 7700 with native resolution 1400x900.. but i can only achieve 1440x900 resolution by using:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
i triyed edit the xorg.conf.. and change the 1440 for 1400 but then it doesnt display in screen resolution preferences
what can i do?
thanks

---

### Post by taurus on 2007-01-30
Did you install nVidia driver for your graphic card?

[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

### Post by overules on 2007-01-30
ye at least it shows a nvidia logo on startup

---

### Post by CocoAUS on 2007-01-30
Make sure you're putting the resolution in default depth line (if default depth is set to 24, make sure your resolution is in the 24 line).  Also, try manually editing your xorg.conf to include the HorizSync and VertRefresh value ranges specified in your montior's manual.  Generally, this is all that needs to be done to get your resolution up to where it should be.  The dpkg-reconfigure method isn't generally very good, so I suggest actually going back to your *original* xorg.conf file that Ubuntu created during the initial install (it will probably be more well-configured), and then inserting the correct frequency ranges in that file.

Hope that helps, I haven't seen it fail yet!

---

### Post by veratyr on 2007-02-09
I'm pretty certain 1440x900 is the native resolution of the a8js.

---

### Post by OvelhaNegra on 2007-02-18
> **overules said:**
> hello.. i have an asus a8js laptop.. with a geforce 7700 with native resolution 1400x900.. but i can only achieve 1440x900 resolution by using:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
i triyed edit the xorg.conf.. and change the 1440 for 1400 but then it doesnt display in screen resolution preferences
what can i do?
thanks

Asus A8Js default resolution is indeed 1440x900 and I have suceeded in using this resolution by means of the line command

sudo dpkg-reconfigure -phigh xserver-xorg

I am sorry I can provide no futher help at now...

---

### Post by xopher on 2007-02-18
Try running nvidia-settings, and selecting the correct resolution there. The app also has an option to 'save the configuration to the xorg.conf file'.

---

### Post by OvelhaNegra on 2007-02-18
> **xopher said:**
> Try running nvidia-settings, and selecting the correct resolution there. The app also has an option to 'save the configuration to the xorg.conf file'.

By the way, how can I run "nvidia-settings"?

ON

---

### Post by xopher on 2007-02-18
In a terminal: ```
nvidia-settings
```

---

### Post by Vencislago on 2007-04-24
> **xopher said:**
> In a terminal: ```
nvidia-settings
```

Thanks... worked with me:popcorn:

---

