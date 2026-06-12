---
title: "Google Earth not responding"
date: 2007-06-23
forum: General Help
---

### Post by grathinam on 2007-06-23
I installed Google earth, no issues there, restarted my laptop, but when I launch Google earth it consumes all CPU and does not respond at all, any ideas what is causing this

Find attached the screenshots

Thanks in advance

---

### Post by mwacky on 2007-06-25
Is your video card configured properly?  I experienced the same problem until my video card was setup properly using Envy.  Post what video card you have then I or someone may be able to point you in the right direction...

---

### Post by swisscow on 2007-06-25
I have an Ati X300 video card and with the radeon drivers, google earth freezes (or sometimes runs but soooo slowly - why it runs sometimes I have no idea). With the fglrx drivers it runs sweet.

Also with Beryl on XGL it's painfully slow as well.

hope it helps - at least you know you are not alone!

---

### Post by IusedTObeSOMEONEelse on 2007-06-25
It uses a lot of RAM, I found adding another stick helped :)

---

### Post by grathinam on 2007-06-26
I have 2 GB of RAM, and I presume my video card is configured properly, is there a way to verify this please let me know.

ATI Video Card

---

### Post by dabl on 2007-06-26
On your system monitor is a "processes" tab -- click that and see which process is eating all your CPU bandwidth.  If it is just GoogleEarth, you'll know that your video card isn't helping much, and probably isn't being used to its capacity.

Another way to see this information dynamically is to open a console window and enter```
 top
```

---

### Post by grathinam on 2007-06-26
Yeap Google earth is what consuming all my CPU, it is hitting 100% and freezes, does not respond at all

---

### Post by dabl on 2007-06-26
You might be running the graphics in "VESA" mode, satisfactory for normal documents and web pages, but not for 3D and acceleration such as used by GoogleEarth.  Search this forum on your specific graphics chip, and see what others are doing to get maximum performance out of it. ;)

---

### Post by grathinam on 2007-06-26
How do I find out am running my Graphics in "VESA" mode

---

### Post by dabl on 2007-06-26
> **grathinam said:**
> How do I find out am running my Graphics in "VESA" mode

OK, for starters, in a console window type ```
glxgears
```, and post your resulting frame rate.

---

### Post by grathinam on 2007-06-27
find attached the screenshots

Thanks

---

### Post by firmwire on 2007-07-10
Decided to post this in more than one forum section:

I have been all over the forums and have found some very good info for possibly solving my issue. I am not sure if it will work or not since I am not at home at the moment. I wanted to run some things by you all to make it easier when I do get home.

Issue: 
Running Compiz Fusion ( perfectly) in xgl w/ gnome. I have fglrx as the driver I am using. I have Composite set to "0" and have even changed it to "false".
When I run glxinfo I get direct rendering is NO. 
glxgears works fine in any session I do.
From what I can find, in order for compiz fusion to run it has to be in xgl mode. But google earth NEEDS direct rendering ( I think).
I think if I just go into a non xgl session the same glxinfo gives me YES for direct rendering. I don't remember though at the moment.
Even so...when I run google earth in any session I get 100% CPU usage from it. It just hangs at the initialization splash screen. I can still kill the process, so it doesn't lock my system up completely. 
I have read that people have been able to get it to work with Beryl and ATI cards running together. I am just trying to figure out how to get it to run with my setup.

In case the question comes up, I have installed it two different ways. I had installed it through Automatix. Then uninstalled it. Then I installed it from the download from the google earth linux download site. Both installs went fine. Both hang and produce 100% cpu usage when activated and hangs on the splash screen.

I found this post [http://ubuntuforums.org/showthread.php?t=176636](http://ubuntuforums.org/showthread.php?t=176636). Do you think this will solve my problem?

Also I have seen posts about libGL.so.1.bz2 and libGL.so.1.tar.bz2, and I do you think this may fix my issue?

Oh yeah... and I even tried this earlier today: DISPLAY=:0 /usr/local/google-earth/googleearth. It just loads the splash screen and hangs.

I know people have had the issue with 100% cpu usage, but I couldn't find anything saying what they did to fix it or if they were even able to.
I have seen in one place that one person actually installed an extra stick of RAM and that helped. But I don't think I should have to. Everything else works great. I only have 1GB on this system currently.

I am running Feisty 64 and it runs completely stable. I love it!

Any suggestions/solutions are greatly appreciated. Thanks in advance.

---

### Post by firmwire on 2007-07-11
/bump

---

### Post by EngDrewman on 2007-07-12
I'm having the same problem. Through my experiments, it appears to be an issue with xgl and/or beryl. I have 2 accounts on my machine, my own and a guest account. My account uses beryl and the guest doesn't. Google Earth fires right up just fine in the guest account, but freezes as everyone is describing in my own account. Executing from the terminal in my account yields the following error message:

drew@linuxbox:~$ googleearth
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
Killed
drew@linuxbox:~$ 

executing via terminal in the guest account yields no such errors

---

### Post by mattalexx on 2008-05-16
Deleted

---

