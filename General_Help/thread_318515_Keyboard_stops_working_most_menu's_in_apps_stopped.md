---
title: "Keyboard stops working most menu's in apps stopped working"
date: 2006-12-14
forum: General Help
---

### Post by Zaggy on 2006-12-14
So yeah, I just had this weird experience.
My keyboard stopped working altogether, my mouse did work, but every menu I could find from my gnome desktop and in firefox didn't work either, including the red shutdown button on the top right.
After a reboot all seems normal again.

I'm running Dapper 6.06, and I have no clue why this happened and what I can do to prevent this :/
I don't use Beryl or anything (I have used it before though).

---

### Post by rlozano on 2006-12-14
what was the last thing you were doing before this happened?

---

### Post by Zaggy on 2006-12-14
Listening to music with Amarok, running XChat2 & Gaim, browsing with Mozilla Firefox.

---

### Post by db9s on 2007-01-22
same thing happens to me, but its after i "lock screen" and use my password to get back in, the keyboard and mouse start acting all weird

---

### Post by Josh_Ovi on 2007-03-05
Hi!

I think I'm not a lot of help here, but I have a similar but different problem. My laptop keyboard stops working sometimes alltogether. When I'm in a konsole, or in vim and I seem to stay to long on a key....

Is there anything I can do about this? Under Windows I have never encountered a problem with my keyboard... So I think is not a hardware problem...

Best Regards Josh

---

### Post by leptogenesis on 2007-05-05
Sorry for digging up an old thread, but I'm getting the same problem on Feisty - sometimes after I unlock the screen (I've set my laptop up to lock the screen whenever I close the lid), the keyboard stops working and all menus stop working...but the mouse, scrollbars, and application launchers work fine.  When I run the terminal, my cursor is that black rectangular outline rather than the black filled-in rectangle (much like you see in a deselected terminal window), even though gnome highlights the window as if it's an active window.  

After a while of playing around, application launchers stopped working (it happened right after I tried to shut down my computer by pushing the red power button on the gnome menu-bar-things).  

Whenever it happens, I can sometimes get it to go back to normal by closing the lid on my computer to re-lock the screen and then unlock it again.

Any ideas?

---

### Post by vronp on 2007-05-08
I have pretty much the same problem.

I have a Dell Inspiron 9400 laptop and once in a while, I will walk up to it and find the keyboard is locked up.  I can move the mouse and sometimes I can use the mouse to do work.

I can force this behavior by pulling my Linksys WUSB54G wireless interface from the USB port.

Usually, I am only running Firefox when the keyboard locks up.

---

### Post by deja on 2007-05-26
I'm having this problem in Feisty Fawn.  

uname -a = 2.6.20-15-generic

on a Dell Inspiron 5150 P4 HT


Many launchers stop working.  Keyboard input ignored.  Mouse works fine.  External keyboard does not work either. 

I'm using gnome but will install KDE to check if it has this problem.  It occurs seemingly at random.

---

### Post by Bonder5678 on 2007-07-15
I've been having the same problem myself on my compaq presario v6000 laptop.  When it has happened, I was running vim, pidgin, and firefox.  Also, I noticed, it seems like when it happens, I also lose my connection to my wireless network, but this could just be coincidence.

But I take it that since no one has posted a fix, no one knows what's going on with this?

---

### Post by yorkie on 2007-07-15
I had same problem 4 weeks ago after taking some actions from forum problem no longer exists actions taken 
1, installed opera browser
2, uninstalled skype
3, stopped using compiz /beryl/fusion
my system has been running o`k since applying above.
hope this is some use to anyone.

---

### Post by jwiener3 on 2007-08-15
any more word on this? I am having the same issue mouse works fine most of the time. I have a dell d620 and am running feisty. I also notice that happens more frequent if I am using terminal services client. Sometimes if I minimize and reopen the windows the functionality come backs. I see  one suggestion was to get ride of compiz/beryl etc... but that is no fun, and I also saw it happen when i was running metacity. Any advise would be great. Thanks

---

### Post by martinnorth on 2007-08-18
Sorry to add another report without really contributing anything, but the more the merrier...

I´ve recent upgraded from Edgy to Feisty Fawn. Never had this issue in Edgy, having it all the time in Feisty Fawn. Same hardware. Not using Beryl or Fusion or anything else unusual. I hope someone is able to discover a root cause.

---

### Post by jwiener3 on 2007-09-05
I think I found out that I was causing my own problem. 
it only happens to me when I hit "ctrl alt d", to show the desktop. While it is in this "showdesktop" mode is when the issue happens. I only open the windows I was looking for, and that is when problem was noticed. I guess the correct way is to his "ctrl alt d" again to bring all the windows back in, seems kinda pointless though. 
Hope that made sense if not let me know and I will try to be more clear :)

---

### Post by leptogenesis on 2007-09-05
> **yorkie said:**
> I had same problem 4 weeks ago after taking some actions from forum problem no longer exists actions taken 
1, installed opera browser

You mean, you stopped using Firefox altogether?  

> **yorkie said:**
> 
2, uninstalled skype


Never had that.

> **yorkie said:**
> 
3, stopped using compiz /beryl/fusion


Never had that either.

> **yorkie said:**
> 
my system has been running o`k since applying above.
hope this is some use to anyone.

My system has been running fine since I installed xubuntu:).  Of course, I hardly ever had it happen...it was once every few months.  Is it some library that has a bug in it - that is, your changes were to make sure that your computer didn't use that library?  Can you point me to the thread that helped you solve the problem?

---

### Post by drewcoll on 2007-09-07
I've got the same problem on my IBM thinkpad.  It usually occurs when it is using the wireless and I am fooling with network manager.  Its very annoying.

---

### Post by FaceLeg on 2007-09-15
I have the same problem, the only "solution" has been to reboot using the button on the case.

Since my computer is very slow, I recently installed FluxBox, which is great by the way.

This strange keyboard/mouse click thing has happened about 5 times, thankfully OpenOffice has document recovery, else I would have lost a damn lot of work.

It has happened when I have had: two or more Bittorrent downloads going + Firefox + OpenOffice + Eclipse + Amarok + aMSN + XChat, or a mixture of those.

3 out of 5 times it has happened while I have been working in Amarok.

Nice to know it isn't just me (before seeing this post I thought it was my BS computer being a sack).

---

### Post by drachenstern on 2007-09-18
Hey there, CS/IT with time to devote to this issue, so any debugging needed, just let me know, even use my nic here as my gmail addy, if you like.

So here's what I've noticed so far on my own system:
+Only happens when my integrated wireless (mini-PCI) dies.
+Seems to have sporadic results when it does happen.
--Generally can be regarded as though the system is reading a long key depress.
---Sometimes is as though I were holding down the spacebar
---Sometimes as though I were holding down arrow
+Using 7.04 base release with regular updates.
+No special devices or software installed except that pesky broadcom 43xx.
+Primarily tends to happen when I am connected to the craptastic APs at uni, never seems to happen with my AP at home.
+Can't hibernate to get out of the problem, have to hard boot.
+Happens on both AC and batt.

POSSIBLY RELATED TO BUFFER - happens when I try to download a lot at one time
POSSIBLY RELATED TO BAD AP BEHAVIOUR - happens when my AP tries to kick me a lot

From reading through these threads, here's what other people are saying:
Happens mostly regarding wireless failure, either over USB or mini-PCI
Keyboard type seems to independent of failure


Simulated elongated keypress seems to make the most sense as relates to the reported failure.  Like I said, I'm CS and IT, (and working on my EE minor under my CS major at uni, so give me a break here, I know this stuff better than 95% of my classmates and 40% of my professors) so I can definitely troubleshoot and help identify, if I were to be presented with possible trial code.  Should my uni classes not be so demanding, I may take a peak at the KB read code, and perhaps towards the wireless network side of the issue, but I am really not that fluent yet in kernel/w-m keyboard reading, so I doubt that I can make a dent in this issue.

As I come across more details regarding this issue, I'll certainly share them, however the odds are not likely that this will be resolved.  The main thing to do at this point is to figure out who all is having this problem on what platforms.  Mostly laptops are at stake right now.

---

