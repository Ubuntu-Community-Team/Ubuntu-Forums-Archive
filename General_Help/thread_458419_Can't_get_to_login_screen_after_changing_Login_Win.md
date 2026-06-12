---
title: "Can't get to login screen after changing Login Window prefs"
date: 2007-05-29
forum: General Help
---

### Post by JuicedJuice on 2007-05-29
Ok, so I was messing around with some login window features and I accidently checked the "Enable Accessible Login" option in System -> Administration -> Login Window -> Accessibility before I restarted. Now, when I try to load up the OS, I get a loading cursor symbol over a black screen that loads forever and I can't get to the login screen regardless of how long I wait. I'm not sure why this option broke the whole OS as i'm fairly new to linux so any help would be greatly appreciated. I'm running Ubuntu 7.04 64-bit. Thanks.

---

### Post by JuicedJuice on 2007-05-29
FIXED (got help in the irc channel)

Had to cntrl+alt+f1 during the infinite loading process, stop the gdm, then startx, then I got booted up ok but couldn't access the login window prefs so had to try starting the gdm in terminal which gave another error and brought me back out of the gui but cntrl+alt+f7 took care of it and I was able to reverse the bad settings and boot up good after restart.

---

### Post by jnewm on 2007-08-25
Thanks so much for posting this.  I got stuck with the same infinite spinning wheel loading, and had no idea why.  I actually thought it had to do with recent updates or compiz fusion.  But when I read your post, I remembered that I'd been messing with the login window settings.  And after following your instructions (except that <ctl+alt+F7> didn't work for me, I had to do <ctl+alt+F2>), I was able to login again!  Thanks again!

---

### Post by kosekiseiji on 2007-08-26
I also have this problem but the above is not working for me...
is there a text config file that can be modified to change the login window back to its defaults?

I can start an Xsession as root and get gnome doing its thing but there is no login window control panel showing up....

any help would be greatly appreciated. I don't want to have to reinstall

- TIm

---

### Post by mik9dt on 2007-08-26
I got things to work as listed in the  thread below .... hope it helps

[http://ubuntuforums.org/showthread.php?t=489210](http://ubuntuforums.org/showthread.php?t=489210)

---

### Post by jnewm on 2007-08-27
Hi Tim, 

Sorry it didn't work for you...   Did you type <gdm> and hit enter in a terminal window before trying?  Also, I definitely had to mess around a lot before I finally got the login window control panel to open---I had to keep hitting <ctl+alt+all the different function keys one by one-i.e. F1, then F2, etc.> until in some graphic interface, somehow, it let me open the login window control panel. 

Sorry I don't know anything else!

PS Did you try the instructions in the post suggested in the reply by mik9dt?

Good luck

PPS If it still doesn't work, try getting help on the IRC channel like the first person.  I bet you'll find an experienced user there who can help you out.  This page tells you how to use the IRC channel, if you don't already know: [http://www.ubuntu.com/support/communitysupport](http://www.ubuntu.com/support/communitysupport)

---

