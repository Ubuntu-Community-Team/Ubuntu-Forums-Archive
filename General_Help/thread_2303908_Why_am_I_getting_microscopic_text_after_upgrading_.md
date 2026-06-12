---
title: "Why am I getting microscopic text after upgrading to 15.10?"
date: 2015-11-22
forum: General Help
---

### Post by Mugsy323 on 2015-11-22
Suddenly, all my dialog text is microscopic. Enlarging the screen text via Ctrl+(keypad+) helps a little, but still much too small, while enlarging everything else right along with it. There does not appear to be a setting to fix it, neither in Ubu or in the nVidia card settings.

I never had this problem before I let Ubuntu upgrade me from 15.04 to 15.10. Any ideas? Help! Thanks.
.

[IMG]http://s6.postimg.org/g1c5kfc1d/Screenshot_from_2015_11_22_16_43_57.png[/IMG]

---

### Post by egeezer on 2015-11-22
Settings > Appearance > Fonts, then change the size

---

### Post by buzzingrobot on 2015-11-22
Install "Unity Tweak Tool" and use it to take a look at font sizes in use. 

Is Nautilus the only app you see this in?

Any PPA's that weren't backed out and disabled before the update?

---

### Post by SeijiSensei on 2015-11-22
1) Boot into recovery mode and choose a root shell when prompted.

2) Make the main filesystem writable again with
```
# mount -o remount,rw /
```

3) Run the program "nvidia-xconfig".  It will write a file called /etc/X11/xorg.conf.

4) Edit that file using "nano /etc/X11/xorg.conf".  Find the "Monitor" section and make this change:
```

Section "Monitor"
    [stuff]
    Option "DPI" "96x96"
EndSection

```

5) Reboot.  You should have decent-sized fonts now.

I have had this problem repeatedly with NVIDIA cards and TVs as monitors.

---

### Post by Mugsy323 on 2015-11-23
> **SeijiSensei said:**
> 1) Boot into recovery mode and choose a root shell when prompted.

I have had this problem repeatedly with NVIDIA cards and TVs as monitors.

*(Sorry for the late reply.)*

That worked! HUGE thanks. That was driving me crazy.

The "DPI" field didn't exist, so I had to add it.

When you run the nVidia Config app from the normal desktop, there is a button to safe your config, but you get a "write access denied" message. If there were a way to write & edit this file from the desktop, you wouldn't need to go through the failsafe command prompt.

Thanks!

---

### Post by Mugsy323 on 2016-03-21
(Follow-up for future reference.)

The problem returned after a driver update when my xorg.conf file was renamed. The fix was to copy my renamed file to xorg.conf using the terminal:

*(In my case, this was: [FONT=Fixedsys]**sudo cp /etc/X11/xorg.conf.03022016  /etc/X11/xorg.conf**[/FONT])*

---

### Post by RobGoss on 2016-03-21
Glad you got it fixed, In the future yoy should use the **Go Advanced,** tab below to use the thumb nail feature because other members have a hard time viewing these larges images.....

---

