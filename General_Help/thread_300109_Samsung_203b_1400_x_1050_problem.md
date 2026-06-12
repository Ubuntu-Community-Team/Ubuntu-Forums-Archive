---
title: "Samsung 203b 1400 x 1050 problem"
date: 2006-11-15
forum: General Help
---

### Post by renard33 on 2006-11-15
Hello there,

I'm trying to configure a Samsung Syncmaster 203b (20 inches)

It's native resolution is 1400x1050 @60Hz (works fine under windows).

I have an I810 chip family (I865) so I use the 915resolution to patch the bios. 

I added the modeline in my xconf (output from: gtf 1400 1050 60 ): 

  # 1400x1050 @ 60.00 Hz (GTF) hsync: 65.22 kHz; pclk: 122.61 MHz
  Modeline "1400x1050_60.00"  122.61  1400 1488 1640 1880  1050 1051 1054 1087  -HSync +Vsync

When I restart X, I have the **correct **resolution, but **the image is shifted right and down**, so 1/3 of the screen is black

Another strange point : the frequency indicated by the menu of the monitor is **45Hz**(and not 60Hz)

I also tried to move the screen with xvidtune, but does not work

Any idea ?
Thanks

---

### Post by morpheus01 on 2006-11-19
Don't know if this will help much but I had problems installing Edgy on my new laptop with Ubuntu - not recognising laptop screen - UltraSharp 1440*900 TFT Display with TrueLife, here's what I did:

In very simple English:

1.plug a normal monitor into my laptop
2.Boot laptop with free Ubuntu installation cd
3.Hold "fn" and "f8" to change default monitor before installing.
4.Install Ubuntu - a cool Linux OS - (once installed you can switch back to the laptop monitor if you wish)
6.Went into the top menu item - system - administration - networking
7.Entered - Configuration = Automatic - the wireless Modem name (Network Name) and Network Password
   (if you were using wireless with Windows before this you'll know these) - this set up the internet.
8.Went to this site - [http://packages.ubuntu.com/dapper/x11/915resolution](http://packages.ubuntu.com/dapper/x11/915resolution)
9.Downloaded the i386 file (the i stands for intel processer - took me a while to figure that out)
10.The driver installed itself much like a windows driver, cool!!
11.I entered in:

Change the settings in /etc/X11/xorg.conf (if using Xorg) or in /etc/X11/XF86Config file (if using XFree86) to:

XRESO=1400
YRESO=1050

 (you need to go to a terminal and type "vi 855resolution" - vi is a unix editor. it's "esc" then "i" to enter text and "esc" then ":" then "wq" then "enter" to exit the editor)

After the comments in the "855resolution" script in the folder that Xpro mentioned above. - had to do a bit of googling to figure this out.

12.Restart the laptop without and hey-presto - started messing around with some of the screensavers
13.Posted this reply listening while my girlfriend called me a nerd.

---

### Post by haelters on 2008-01-21
[http://ubuntuforums.org/showthread.php?p=4180275#post4180275](http://ubuntuforums.org/showthread.php?p=4180275#post4180275) helped me

---

### Post by sidbcn on 2008-01-21
Maybe this solution is too simple for words, but I stumbled upon it by accident.

I had to reinstall Ubuntu as when mounting my second 500GB HDD the start up drive got screwed up in /etc/fstab and a bunch of other directories and stalled in Busybox. Easiest was a reinstall, as even some guru's did not have the full explanation on how to recover from that error.

I found out that with both the VGA and the DVI cable connected to the 203b, the install works perfectly. No extra pixel rows and no extension on the right.You need to have both cables connected as parts of the install work via VGA and only upon later installation can you receive a signal via the digital cable.Without both connected the first part of the install would give a black screen.

Somehow the install reads the type of monitor you have via the digital cable and finds the right driver package to match it.

Before this I just had the VGA cable connected and the install just gave the 1280x1024 option, which gives a blurred screen. Make sure you connect the screen before you start up the CD as it reads the resolution very early in the CD boot.

Hope this helps. I guess that if you want to set 203b up as a second screen on a laptop it is harder, but the desktop users will like this solution I am sure.

Good luck with the learning curve. I have certainly spent about a 1000% more time on Ubuntu installation than I thought beforehand. Nice, but only if you can spare the time.:lolflag:

---

