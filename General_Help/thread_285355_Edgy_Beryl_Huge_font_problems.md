---
title: "Edgy Beryl Huge font problems"
date: 2006-10-26
forum: General Help
---

### Post by anomalz on 2006-10-26
I just did a fresh install of edgy and i just installed beryl. everything works fine except when i am in the XGL session, the fonts are huge! and i can't change the themes in System>Pref>theme or in the system>pref> fonts. I had it running fine in dapper and i could change the theme. If i attempt to change the theme, nothing happens, but if i log into the normal gnome session, the theme is changed there. The emerald themes work fine, and there is no option for fonts in the beryl/emerald settings. I went back over the instilation and checked all the config files i had to edit/make and everything looks like what i was told to put in there

Any advice?
<specs>
IBM thinkpad T60
Core duo 1.83ghz
Ati x1300
1gb ram

---

### Post by Edowardo on 2006-10-28
I have the exact same problem and it's driving me up and off the wall! Also my audio isn't working once XGL and Beryl where installed. :\ Once I get these problems fixed I need to setup my power management options next. Then it's VMware time! :3

Anomalz is your audio working? We should have the same audio card I think..? Also what have you accomplished with your T60 drivers can you get everything functioning including all function keys and features? Maybe even that cool IBM HDD shock protection feature?

Thanks

[almost same specs]
IBM T60
Core duo 2.0ghz
ATI x1400
2GB DDR2

---

### Post by anomalz on 2006-10-29
Cool, at least someone else has the same problem.. 
My T60 has the x1300. but yeah my audio works with it., just the freaking fonts are huge. it's usable but it bugs the crap outof me cause im used to my crisp 1400x1050 with nice small fonts.
as for my thinkpad, i read a few articles on it and there are ways to get all the Fn keys working. i managed to get my trackpoint working the way i need it to. if you google "Ubuntu 6.06 on X60" there is a tutorial on alot of the stuff that worked for mine. my next big task is to get the fingerprint reader working and the Active protection stuff working...

---

### Post by kuckus on 2006-10-29
anomalz,
what version of the ATI driver did you use? The package provided at ati.(amd.)com didn't work for me, and now, using the one from the Ubuntu repositories, fglrxinfo still returns

> Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)


for me. Which leaves leaves me wondering if it is worth trying to get beryl working at this point or if there is still something missing in my xorg.conf. I am on an x1300 as well. 

Would you mind sharing your "Device" section of xorg.conf? 

Thanks!

---

### Post by kuckus on 2006-10-29
Okay, I now managed to get it to work following this write-up:

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_8.29.6_drivers_in_Ubuntu_Edgy_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_8.29.6_drivers_in_Ubuntu_Edgy_Manually)

Cheers/kuckus

---

### Post by anomalz on 2006-10-29
Thanks, im gonna try it out now

---

### Post by anomalz on 2006-10-30
no luck.. still the same fonts problem.. w/e.... i'll wait a bit and try again when the update it next

---

### Post by Edowardo on 2006-10-30
Okay my Ubuntu Edgy/Beryl/XGL home slices, I figured it out! It's the dpi configuration in XGL startup. 

XGL goes to auto default dpi 120 or something. I realized it when I was nosing around in my Xorg.conf file. I realized that the Xorg.conf and the ATI drivers were fine; since I was running at 1400x1050 and the desktop fonts would actually change size when I told them to. So I knew it came directly from XGL and it's graphic settings. Beryl is just a program it doesn't really control resolutions and stuff... I think... heh I'm still new to linux. Anyways here's the answer.

Open up your terminal and enter in the following:
```
sudo nano /usr/bin/startxgl.sh
```
Once your in, enter the code *[COLOR="Red"]**-dpi 96**[/COLOR]* in the Xgl line. You should see something similar to this one complete:
```
#!/bin/sh
Xgl -dpi 96 -fullscreen :1 -ac -accel glx:pbuffer -accel xv:pbuffer &
sleep 4
export DISPLAY=:1
exec gnome-session
```

Save your settings and reboot. Tada! Fixzorz! Enjoy!

---

### Post by Lesterchakyn on 2006-11-16
I recently found out how to fix this problem, using both gnome and kde.

In your Xgl startup script, the -dpi XX can help, but the session start is the troublemaker.

We should change the "exec gnome-session" or the "exec startkde" lines for the following:

exec /etc/X11/Xsession

It will take care of the default fonts and mouse cursors.

---

### Post by nhidog on 2006-11-16
Thanks -dpi option did the trick.  I was wondering why the heck my icons were so freakishly big.  Now does anybody know how to change icon theme within Beryl?

Thanks,
Nhi

---

