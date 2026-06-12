---
title: "Ubunutu doesn't detect monitor through VGA switch box."
date: 2013-08-16
forum: General Help
---

### Post by GameGuru on 2013-08-16
Ok I have my PC running through a nice VGA switch box because I have my Xbox 360 hooked up to my monitor also.  Ubuntu wasn't automatically seeing my monitor and I was locked into 1024x768.  Doing some research for my Acer x193w I found Ubuntu should be reading it fine when I put it on User.  I wondered about the switchbox so I did a direct connect to the monitor and Ubuntu recognized it and I could go max resolution.  I then hooked it back through the switch box and it dropped back down to 1024x768.  I didn't have a problem with this in Windows 7.  Can I lock it somehow at this resolution so when I put it through the box it stays?

---

### Post by tgalati4 on 2013-08-16
Many switchboxes have a resolution and refresh frequency limitation.  What is the exact resolution and refresh Hz that you use in Windows?  Put those entries into *gtf* and then cut and paste into your /etc/X11/xorg.conf file.

tgalati4@Mint14-Extensa ~ $ gtf 1600 1200 60

  # 1600x1200 @ 60.00 Hz (GTF) hsync: 74.52 kHz; pclk: 160.96 MHz
  Modeline "1600x1200_60.00"  160.96  1600 1704 1880 2160  1200 1201 1204 1242  -HSync +Vsync

Paste it into Section "Monitor".  Logout or reboot.

---

### Post by GameGuru on 2013-08-16
1440x900 @ 75Hz

Can you walk me through setting this up like I am new (I am).  What is GTF?

---

### Post by tgalati4 on 2013-08-16
Open a terminal:

```
gtf 1440 900 75
```

It might look something like:

tgalati4@Mint14-Extensa ~ $ gtf 1440 900 75

  # 1440x900 @ 75.00 Hz (GTF) hsync: 70.50 kHz; pclk: 136.49 MHz
  Modeline "1440x900_75.00"  136.49  1440 1536 1688 1936  900 901 904 940  -HSync +Vsyn

Use the mouse to highlight the two lines and hit Shift-Control-C to copy.

Verify that you have an xorg configuration file:

```
cat /etc/X11/xorg.conf
```

If you don't have this file, then you will have to create it.  Log out and log into a Rescue Shell from GRUB.

That will take you to a root console and run:

```
X -configure
```

That should create an /etc/X11/xorg.conf file that you can add your modeline to.

```
reboot
```

Log back into your normal desktop.

Add the above 2 lines (copy and paste) into xorg.conf using:

```
gksudo gedit /etc/X11/xorg.conf
```

Put the lines under the Section "Monitor" then reboot.

Test your vga switchbox.

I'm running 12.10, so there may be slight differences with 13.04, but give it a try.

---

