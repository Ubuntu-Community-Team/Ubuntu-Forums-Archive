---
title: "Widescreen Monitor"
date: 2008-05-05
forum: General Help
---

### Post by jakeruston on 2008-05-05
Hi,

I'm just installing Ubuntu now from a Live CD, at this very moment. However, my monitor is a widescreen, and the demo and installation is being displayed very oddly, with a big black gap on the left, and Ubuntu not fitting on the screen.

How can I change Ubuntu to display correctly on a Widescreen?

Thanks,
Jake Ruston.

---

### Post by chewearn on 2008-05-05
What graphics card do you have?

---

### Post by jakeruston on 2008-05-05
I think this is the Graphics Card - GeForce FX 5200.

---

### Post by chewearn on 2008-05-05
After you finish install, upon first boot, enable the nvidia restricted driver here:
Top panel menu > System > Administration > Hardware Drivers

---

### Post by jakeruston on 2008-05-05
I did so, and did the reboot as it said, but now when it is loading up again, I get this message:

Out of Range
H: 68
V: 85

In a small blue box with a black background.

How can I fix this?

---

### Post by chewearn on 2008-05-05
Press CTRL+ALT+F2.  Do you got a console login prompt?

If yes, log in using your username and password.  Then, run this command:
```
sudo nvidia-xconfig
```

Then reboot.  Please post any error you encountered.

---

### Post by chewearn on 2008-05-07
Turn on your sound, when you get to the monitor out of range situation, did you still hear the drumroll, which indicate you are at the login screen?

If you did, type in your username<enter> and password<enter>.  Hopefully you will now be able to see your desktop.

If it goes as according to the description above, this link might help you get back the login screen:
[http://www.namanb.com/2007/11/ubuntu-710-bootup-resolution-problem.html](http://www.namanb.com/2007/11/ubuntu-710-bootup-resolution-problem.html)

Note:
The link works most of the time for gutsy, I haven't got any info about success rate in hardy.  But it's worth a try.

---

### Post by jakeruston on 2008-05-07
I heard the drumroll, and managed to login, but still didn't see the desktop.

---

### Post by chewearn on 2008-05-07
It looks like we have to manually fix the xorg.conf.  Press CTRL+ALT+F2, login into text console (I hope the monitor can show that, at least).

Copy the xorg.conf file into an external media like USB flash, so you can post the file here.  I hope you knows a little bit of command line.

Copy:
```
cp <source> <dest>
```A USB flash media, when plugged in, will show up under /media/<subdir>/, usually /media/disk

E.g.
```
cp /etc/X11/xorg.conf /media/disk
```

---

### Post by jakeruston on 2008-05-08
Okay thanks, I managed to grab the file.

[http://www.jakeruston.com/xorg.conf](http://www.jakeruston.com/xorg.conf)

I uploaded it there so you can access.

Please let me know what to do next.

---

### Post by chewearn on 2008-05-08
Ok, I need to find out your monitor specs.  Try find out as much info as possible.

1. Pixel resolution
2. Refresh rate

Meanwhile, change the following parameters to a more reasonable values (this just a trial error approach):

Locate: Section "Monitor"

Change from:
```

    HorizSync       10.0 - 70.0
    VertRefresh     20.0 - 160.0
```

To:
```

    HorizSync       30.0 - 70.0
    VertRefresh     40.0 - 80.0
```

---

### Post by jakeruston on 2008-05-08
Wow, simply changing those numbers fixed it!

Thanks!

---

### Post by chewearn on 2008-05-08
Glad it finally worked.  \\:D/

.

---

### Post by Gordon Weast on 2008-05-08
I have a similar problem with my Dell widescreen monitor.  I have the E198WPF monitor that has a native resolution of 1440x900.

This monitor has an 'Auto Align' function on the onscreen menu.  If your monitor has this function, try invoking it.  See if that corrects the location of the active video.

My problem shows up when I alternately boot into Windows or Linux.  If I have the screen correct in one system, then boot into the other, the visible desktop is shifted either right or left, depending on which system was active when I last did the Auto Align.

I suspect that this is due to the sync polarity being different in Windows than in Linux.  I've been unable to get the Linux X server to switch it though.  In Windows, there's no hope of switching the sync polarity.

---

### Post by chewearn on 2008-05-08
> **Gordon Weast said:**
> I have a similar problem with my Dell widescreen monitor.  I have the E198WPF monitor that has a native resolution of 1440x900.

This monitor has an 'Auto Align' function on the onscreen menu.  If your monitor has this function, try invoking it.  See if that corrects the location of the active video.

My problem shows up when I alternately boot into Windows or Linux.  If I have the screen correct in one system, then boot into the other, the visible desktop is shifted either right or left, depending on which system was active when I last did the Auto Align.

I suspect that this is due to the sync polarity being different in Windows than in Linux.  I've been unable to get the Linux X server to switch it though.  In Windows, there's no hope of switching the sync polarity.

Normally, a good monitor will store separate alignment settings based on resolutions and refresh rates.  If you run Windows and Linux with the same resolution, then you should use different refresh rates for each OS.  That way, the monitor will store unique alignment settings for each OS.  E.g. if you run linux at 60Hz, then run Windows at 65Hz.

---

