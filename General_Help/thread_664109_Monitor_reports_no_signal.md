---
title: "Monitor reports no signal"
date: 2008-01-10
forum: General Help
---

### Post by tech.roberts on 2008-01-10
I have Gutsy 7.10 installed and everything has been working great.  I had Compiz with twirling cubes and eye candy galore, yee hah.   But I like to tweak stuff and I decided to manually configure a dual monitor setup (did not use Userful).   I actually got that working OK.  At least to the point that I had both monitors showing the same X session, no Xinerama, just two monitors showing X.  I shut the system down for the night and since I really did not need a two monitor setup I disconnected one of the monitors.  Since then I have not been able to get back to an x session. The boot process goes past the GRUB screen then the monitor indicator light goes from green to amber and the monitor reports no signal.  I can access the recovery mode fine. 

Video card is an Ati Radeon 9250 dual headed.  I have followed the suggestions that others have posted.
I have reconfigured the xserver choosing the vesa driver , examined my Xorg.0.log file for errors, examined my Xorg.conf file for typos,  etc. but still can't get into an x session.   Prior to starting my tweaking I had backed up my Xorg.conf file but even restoring that backup does not help.  

Any suggestions?  Have I overlooked something?

---

### Post by renfrew on 2008-01-12
I've had similar problems with my radeon 9250 (haven't actually got dual-head working yet though). I had to boot into recovery mode (no gui/X) from the grub menu.  

Once there I was able to issue the Startx command from root command prompt and watch the XServer load.  

I ended up running sudo dpkg-reconfigure Xserver-xorg.  the dpkg-reconfigure installs all the defaults so you'll lose your dual-head .conf, but you should be able to see where its failing with startx and may not have to reconfigure...

---

### Post by tech.roberts on 2008-01-12
Thanks.  I gave your suggestion a try. After typing startx I get a quick flash of the screen, then a few seconds later the monitor reports no signal, and about ten seconds after that the monitor status light goes from green to amber and at that point nothing happens no matter how long I let it set.  /var/log/Xorg.0.log has no errors in it.  I did the dpkg-reconfigure and have same issue.  I also tried a different monitor with same result.  I am going to try a different video card, reconfigure xorg, and see what happens.

---

### Post by tech.roberts on 2008-01-12
I tried a known good video card with no change in problem.  At this point I knew the card and the monitor are good so I focus on my conf and log files.  I do not see any obvious problems however in the process of looking I discover a number of libraries that X uses linked back to my usr/local/lib directory and like a bolt of lightning I am hit with the sudden memory of that Xephyr install I did when I was trying to get dual headed to work.  I deleted Xephyr and bingo back in action.  Well almost, Compiz is dead, and virtual terminals are dead (they have actually been dead for a while now and I have been following threads that other with this problem have posted.)  Why I forgot about the Xephyr install I don't know I usually write down stuff I do for just this reason but I got lazy.

Thanks to renfrew for the help.

---

