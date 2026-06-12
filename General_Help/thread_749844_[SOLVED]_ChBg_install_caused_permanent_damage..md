---
title: "[SOLVED] ChBg install caused permanent damage."
date: 2008-04-08
forum: General Help
---

### Post by bilijoe on 2008-04-08
I recently installed ChBg hoping to use it to change my desktop background periodically--apparently a serious error.  I carefully set all the options in what seemed to be the correct way to get it to do what I wanted.  Once I started it, however, I began to get a significant amount of anomalistic behavior from the system.  Every few minutes, except for the window that had focus, the entire screen would go black.  After a moment, the screen would flash, momentarily display one of the images selected to be used as a background, flash again, restoring the "standard" background (i.e., the one I had been using before trying this experiment), and my Home Folder would open.  Then, sometimes (but not always) the system would either go into standby, go into "limbo", or return to the log in screen.  Sometimes, just moving the cursor into an area, a couple of square inches in size, in the upper left hand corner of the screen, would cause my Home Folder to open.  When I shut down and restarted, after the Ubuntu logo screen appeared, a white line, one character space high, would appear across the entire screen, covering the bottom part of the logo, and the system would take an abnormally long time to boot up.  After logging in, I found the strange behavior was still occurring. So, I did a "complete uninstall" on ChBg, and rebooted.  The white line still appeared, the system still takes unusually long to boot, and, when the power management system puts the computer to "sleep" from inactivity, it goes into a strange coma-like state.  Neither mouse nor keyboard activity will wake it up (as it used to do).  The only thing that gets its attention is pressing the power button, but when I do that, after some disc activity, and lights on the keyboard flashing, the screen displays the background image only--no icons, no panels, sometimes my Home Folder opens briefly, and then the computer shuts down.  HELP, somebody, please!  What kind of a mess have I created here, and can I fix it?  If this were Windows, I'd format the disc, and reinstall the system, but I had hoped one of the things I was getting away from by switching to Linux was the need to ever have to take such drastic measures again.  Since I have so many symptoms (white line across logo screen, abnormally long boot times, Home Folder opening for no apparent reason, odd behavior when the computer goes to sleep), I have NO IDEA where to even start.  I hope somebody out there can help me.

---

### Post by SPr on 2008-04-09
I have no idea what's happening either :( Have you looked in the logs for any errors? Becuase the list of problems is so long I'd look in them all.

Could this be caused by hardware failure? Could it be just coincidence that hw started to fail just after installing chbg? I'm just thinking out loud.

I take it you haven't made any backups so restoring a backup is out of the question.

If you have uninstalled this program does
```

sudo apt-get autoremove

```
show any unused files (libraries etc) that can be removed? (Still thinking out loud... I've no idea why that would help but worth trying anyway).

---

### Post by bilijoe on 2008-04-09
Thanks for taking the time to "think out loud", and document your thoughts for me.  "sudo apt-get autoremove" did, in fact, find four files laying around that it said were no longer needed.  I don't know if they are related to ChBg, but since it is the only thing I have ever removed, I think chances are good.  FYI, the files were: 
 libgdk-pixbuf2 ...
 libgtk1.2 ...
 libglib1.2 ...
 libgtk1.2-common ...

Time will tell if removing these fixed anything.  I'll let you know.

Thanks again.

---

### Post by bilijoe on 2008-04-11
Well, I haven't had any strange behavior from my system in a couple of days, except for FireFox, which appears to be a problem unto itself (see "FireFox Misbehaving" in the General Help forum, *please*).  Running ```
sudo apt-get autoremove
```appears to have done the trick w/ regards to the other odd behavior I was experiencing.  Thanks again to SPr for "thinking out loud".

---

### Post by SPr on 2008-04-12
> **bilijoe said:**
> Well, I haven't had any strange behavior from my system in a couple of days, except for FireFox, which appears to be a problem unto itself (see "FireFox Misbehaving" in the General Help forum, *please*).  Running ```
sudo apt-get autoremove
```appears to have done the trick w/ regards to the other odd behavior I was experiencing.  Thanks again to SPr for "thinking out loud".

Well, I hope it remains like that. I have no idea why removing unused libraries would do anything in this case thuogh.

---

