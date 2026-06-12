---
title: "Wallpaper missing"
date: 2008-05-13
forum: General Help
---

### Post by beerguzzler on 2008-05-13
I've been using Hardy now for a couple of weeks without any major issues.

One thing that has happened just today, my wallpaper is no longer displayed.

The picture is selected in the Background tab but all that is displayed is the black background from the theme.

I've tried changing to a different picture, even added a new one but no matter which one I choose, none of them display.

Not the end of the world, but would be nice if it can be fixed.

Cheers.

---

### Post by macaholic on 2008-05-13
If you don't have a super customized nautilus, you could try reconfiguring it with```
sudo dpkg-reconfigure nautilus
```

---

### Post by beerguzzler on 2008-05-14
Thanks but no change.

I've tried alt+f2 and running gconf-editor show desktop is selected in apps/nautilus preferences.

Absolutely nothing is displayed on the desktop, simply a black screen.

---

### Post by beerguzzler on 2008-05-14
Sorted. Answer was on another thread - [http://ubuntuforums.org/showthread.php?t=664522](http://ubuntuforums.org/showthread.php?t=664522)

Mine was a little different my %gconf.xml was in $HOME/.gconf/apps/nautilus/ There was no desktop folder. Simply created the folder and moved the %gconf.xml file into it.

---

### Post by kubiutsa on 2009-07-11
Hi, i have a similar issue on Kubuntu 8.10 (using KDE), basically my wallpaper suddenly disappeared, the desktop just got white-grayish, and i can't seem to be able to restore it ever since. (I was using the default Blue Curl one). I tried reebooting, recovery mode, logging as another user, creating new user and logging as it, neither worked, always the white screen. Everything else seems to have remained intact (widgets, icons, splash screen, panels...)
If i right-click on desktop and go to Desktop Setting, the wallpaper is selected but not visible in preview. If i browse to any other image it doesn't show either, just white desktop again.
I found the right image (1920x1200.jpg) in /usr/share/wallpapers/Blue_Curl/contents/images but i don't know how to restore it...
Can anyone help with this? 

Thanks

---

### Post by zapstrap on 2009-07-22
Same problem here.  I'm running Mythbuntu 9.04.  For no reason I can find, the machine booted up last night with no wallpaper, no desktop icons, and no applications menu when I right-click on the desktop.  If I go into the desktop settings, the background image still shows what I had yesterday, "show applications menu on desktop right click" is checked, and several default icons are checked.  I get a black screen with the panel at the top, and that's it.  I looked in the Desktop directory, the only things there are files called app.desktop (firefox.desktop, xine.desktop, etc).  Can anybody suggest what might have gone wrong?

Also, beerguzzler: the link you listed is broken.  I'd like to see the thread you found.  Any chance you could correct it?

---

### Post by zapstrap on 2009-08-11
Anybody?  It seems like a bit of a defeat to just "learn to live with it" when it was working before.  

This is a mythbuntu box, and because of the Panasonic display overscanning, the panel is not visible on the screen.  I have to guess at the location to find the apps button.  Having desktop icons is a good enough workaround for this problem.

I also have no menu when I right-click on the screen, even though the configuration checkbox for the applications-menu-on-right-click is checked.

Seriously, anybody?  Please help?!?

---

### Post by running_rabbit07 on 2009-08-11
Did you try booting into restore mode and "fixing broken packages?"

Edit: Last time I had a problem like that was when I was trying to install FF3.5 and it screwed everything up and nobody could help, I just reinstalled.

---

### Post by zapstrap on 2009-08-11
Yes, I tried it, no luck.  I upgraded to ff 3.5 too, but I got the source, compiled it, and just changed the symbolic link in the /usr/bin directory to point to v3.5.  This works, but I'm still stuck here.  I'd really rather not resort to starting again from scratch, as it would be the third time I've had to burn the house down due to no solution.  I checked all the settings I can find, and it looks like I should have wallpaper, along with several icons, but I get nothing.  This happened about 2 weeks after the Nvidia driver just mysteriously ate itself too.  I never got so much as a lick of response on that query either.  I don't want to give up, but what's your time worth?

---

### Post by dcstar on 2009-08-11
> **zapstrap said:**
> Yes, I tried it, no luck.  I upgraded to ff 3.5 too, but I got the source, compiled it, and just changed the symbolic link in the /usr/bin directory to point to v3.5.  This works, but I'm still stuck here.  I'd really rather not resort to starting again from scratch, as it would be the third time I've had to burn the house down due to no solution.  I checked all the settings I can find, and it looks like I should have wallpaper, along with several icons, but I get nothing.  This happened about 2 weeks after the Nvidia driver just mysteriously ate itself too.  I never got so much as a lick of response on that query either.  I don't want to give up, but what's your time worth?

If you are having multiple unrelated problems with your system where others have no problems at all, then it is something in **your** environment.

You either have faulty hardware or something else that is corrupting your system, it is not an issue of recompiling/reinstalling things that should never, ever need this done.

---

### Post by zapstrap on 2009-08-12
I'm definitely having a hardware problem.  I tried installing fresh on a separate hard disk.  I removed the old one.  The broken nvidia driver is still broken.  If I install the video card in a separate machine running winxp, the video card works 100%.  I ran memtest, no errors were found.  This leaves the processor or the motherboard.  I doubt the processor is the problem, as so much does appear to be working properly.  A motherboard problem seems likely.

With the fresh install, the background image and applications menu on right-click both work.  If I put the original drive back in, they don't.  This is not a hardware problem, and is what I'm trying to resolve.  The trouble is, every place I look within system settings and log files, doesn't reveal any error.  The checkbox for showing the applications menu on right-click is checked, but there's no menu unless I click on the button on the panel.   A background image is selected, but does not appear.  I get a black screen with a panel, and that's it.

---

### Post by zapstrap on 2009-08-16
I replaced the motherboard (swapped Asus P4P800-vm for P4P800-E), all's well with the nvidia driver now.

I still have no wallpaper, or desktop icons, or menu on right-click.  Looking in desktop settings shows these things all enabled.  If this is a problem in my environment, or something corrupting my system, is there a correct place to look?  I've tried looking in some of the system logs, no luck.  The only warning I could find in the Xorg.0.log file was about disabling keyboard0 and mouse0.

Can anyone point me to where I might look to find out why these things have stopped working?  Is this a failure to load something in the desktop?

---

### Post by zapstrap on 2009-08-18
Found it. :)  

xfdesktop is not running at X session startup.  I launched it manually from a terminal session and logged out, saving session settings.  When I log back in, it's all good.   This seems like a tenuous way of getting the desktop manager to run.  Is there a place, somewhere in the user .config directory, or similar location, where this is supposed to be launched?

---

### Post by HiImTye on 2009-08-18
wow that sounds like a lot of trouble. I would have just started over if I got all that. you, my friend, have much more patience than I

---

### Post by stinger30au on 2009-08-18
for wall papers i use wall paper tray

sudo apt-get install wallpaper-tray

once installed got to the top bar of the screen where it says appliactions, places, system etc

right click on a  blank bit and press 

add to panel


now scroll down and find wall papar tray and add that


u will see a small icon appear on the panel now

right click it and click preferences

set the timer to anything other then zero or it will go nuts

then point it to the directorys u have with photos and let it rip

u may find on startup it does not autostart

easy fix

restart the pc and log in

add wallpapaer tray to panel

click system
clcick start up aplications

click options and put tick in box

restart pc
go back into to startup applications and options and remove tick

restart

now it should be all good with wallpaper tray stuck there on startup & run everytime

---

### Post by zapstrap on 2009-08-19
Thanks for the detailed instructions.  Unfortunately, selecting the wallpaper was never the problem.  I expect wallpaper-tray will happily select wallpaper for display, but without xfdesktop running, it will never display.  The only reason I even had a panel was that I manually added one prior to xfdesktop somehow failing to start.  Now that xfdesktop is launching, wallpaper is displayed as expected.

The question is, which config file does one edit to ensure xfdesktop launches after user login?  I looked around a bit at the xfce4 forum site, and it appears this is not that unusual of a problem.  What I didn't see there is an answer to my question.   What I did, manually launching xfdesktop from a terminal, then logging out with save session checked, seems to be the fix.  I still can't believe this.  Shouldn't it be in a script file somewhere?  It must be, as   xfdesktop launches properly from new user accounts.  Would this thread be better served on the xfce4 forum?

---

### Post by zapstrap on 2009-08-19
> **HiImTye said:**
> wow that sounds like a lot of trouble. I would have just started over if I got all that. you, my friend, have much more patience than I

Well, hindsight is 20:20, but don't mistake laziness for patience :). Other than this little annoyance, the machine has been quite usable as a media centre.

---

