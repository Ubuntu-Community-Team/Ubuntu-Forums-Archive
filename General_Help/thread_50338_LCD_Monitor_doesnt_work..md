---
title: "LCD Monitor doesnt work."
date: 2005-07-19
forum: General Help
---

### Post by kasios on 2005-07-19
Hi, I wanted to try the live cd but my lcd monitor doesnt seem to work.  Everything loads up, I hear sounds and everything but the monitor says "no signal". It's a 19inch benQ and its connected with DVI.  Any ideas?
Thanks.

---

### Post by audax321 on 2005-07-20
There's not much you can do if you can't make it to a console screen. Try some of the following and see if any of them drop you to something that looks like DOS or the command prompt in windows:

CNTRL+ALT+BACKSPACE
CNTRL+ALT+F1 to F6


You may need to push enter when the screen appears and it will ask you to login. I believe your username on the LiveCD is just ubuntu and there is no password, so you can just push enter when you get to that.

If you can get that far... post the model number for your monitor and then we can try to help by finding the vertical/horizontal sync frequencies for it and walking you through entering those in /etc/X11/xorg.conf and restarting x.org. That should let you into the LiveCD unless its some other problem...

---

### Post by Bubbasheeko on 2005-07-25
I have the same issue, but I it's not an LCD.  I have a TVM AS6S running on an ATI All-In-Wonder 128 w/tvout.  Not sure if the Live CD has built in support for either.
I would appreciate any help.

---

### Post by kasios on 2005-07-25
sorry for the late response.  yes I got on to the dos type thing with crt+alt+f2.  My monitor is BenQ FP937s.

Thanks for any help.

---

### Post by marr on 2005-08-05
My LCD (Neso LD500V) doesn`t support ubuntu too :( my video card is NVIDIA GeForce4 MX 440 with AGP8X, when I am trying to start live CD screen turns off and there stays out of range H:31 kHZ V:59 Hz ... so... is there something we can do to use ubuntu?
Thanks in advance.

---

### Post by nocturn on 2005-08-05
I think that the problem is caused by Ubuntu not being able to detect the supported resolutions on your monitors correctly.  I don't know how to fix this for the LiveCD though.

---

### Post by marr on 2005-08-06
The same problem is with the install CD... I can not install ubuntu somehow being blind :) ... maybe I have to find another monitor, connect it, then install ubuntu and then change the resolution... how is it there with changing it? is it possible?

---

### Post by pszilard on 2005-08-06
I too have similar problems. I tried running the Live DVD on a new Dell Inspiron 6000. I checked in XP what the resolution was (1680x1050) so when Ubuntu asked what resolution I wanted, I chose that, however at the end of the boot it just had a blank screen :( very disappointing.

I then tried on a Dell Optiplex SX260 which is connected to a 1024x768 LCD. This it it all booted and screen worked - but only at 800x600 and would not allow any other mode. I then tried my Knoppix Live CD and it went perfectly, operating at the 1024x768 resolution.

This is very disappointing, just when I am falling in love with Ubuntu!

-paul

---

### Post by georgebastille on 2005-08-07
When I installed Ubuntu and tried to get my Radeon 9500pro working using the fglrx drivers, my monitor (17 inch CPT LCD) came up with a message saying 'Out of Range'. This was strange because I had set up the refresh rates (or so i thought) in xorg.conf. It turns out however that the DDC info my monitor was telling my graphics card was wrong and xorg was using this DDC info over what I told it. The solution was to add the line:

 	Option		"NoDDC" 		


to the Device section of xorg.conf and make sure that the HSync and VRefresh setting are accurate.

This then solved my problem and my monitor is working at full resolution with no problems.

Hope this helps

---

### Post by marr on 2005-08-08
Then teoreticly is it possible to change the resolution later... there stays only 1 problem - to find a temp monitor for installation time :) ... 
anyway - thanks, I`ll keep trying...

---

### Post by heimo on 2005-08-09
I don't know if this is of any help with Live CD resolution problems, but hopefully it can help someone on this thread:
[http://ubuntuforums.org/showpost.php?p=129379&postcount=21](http://ubuntuforums.org/showpost.php?p=129379&postcount=21)

---

