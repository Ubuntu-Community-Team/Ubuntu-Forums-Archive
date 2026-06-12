---
title: "Flash works, but it has no audio."
date: 2007-05-16
forum: General Help
---

### Post by iAlta on 2007-05-16
So I got flash working with EasyUbuntu, but audio in flash movies and flash websites don't work. (Audio in general works)

Could anyone help me, please?

---

### Post by LuisGMarine on 2007-05-16
Download the package named *alsa-oss* , use synaptics, apt-get, or aptitute, doesn't matter, just get and install the packages.

Then:
```
sudo gedit /etc/firefox/firefoxrc
```

Change the line:
```
FIREFOX_DSP="none"
```
to
```
FIREFOX_DSP="aoss"
```

Restart the browser and try again.

Hope this works!

---

### Post by iAlta on 2007-05-17
I got the same response from YouTube support and it didn't work, sorry.

---

### Post by jslmg on 2008-01-17
> **LuisGMarine said:**
> Download the package named *alsa-oss* , use synaptics, apt-get, or aptitute, doesn't matter, just get and install the packages.

Then:
```
sudo gedit /etc/firefox/firefoxrc
```

Change the line:
```
FIREFOX_DSP="none"
```
to
```
FIREFOX_DSP="aoss"
```

Restart the browser and try again.

Hope this works!

Did this on Gutsy, but it had no effect. Is there a similar, but different change for Gutsy? 

Lots of people are asking the same question over and over again, actually. One neat fix could solve it all.

---

### Post by jslmg on 2008-01-17
> **jslmg said:**
> Did this on Gutsy, but it had no effect. Is there a similar, but different change for Gutsy? 

Lots of people are asking the same question over and over again, actually. One neat fix could solve it all.

OK, I found the one neat fix. Download this:

[http://www.paulbetts.org/projects/libflashsupport_1.0~2219-2_i386.deb](http://www.paulbetts.org/projects/libflashsupport_1.0~2219-2_i386.deb)

Found at Launchpad bugs page. I should 'a' looked there first!

---

