---
title: "Satellite A215-S5818 help"
date: 2008-01-07
forum: General Help
---

### Post by fissionmailed on 2008-01-07
Ok, I got a new laptop today,  I got home and install Ubuntu (can't stand Vista). Here's the rub, the graphics aren't perfect, no sound and the wireless isn't working.  
[http://www.toshibadirect.com/td/b2c/rdet.jsp?seg=HHO&poid=405001&cm_sp=Navigation-_-RecentlyViewedItems-_-ItemLink1](http://www.toshibadirect.com/td/b2c/rdet.jsp?seg=HHO&poid=405001&cm_sp=Navigation-_-RecentlyViewedItems-_-ItemLink1)
Link if you like.
I tried to fix the sound and graphics ( I can use wired internet for now) with some of the threads here but I kept running into walls so to speak.

It shows up under restricted drivers, but I get an error.
"The software source for the package

xorg-driver-fglrx

is not enabled"

Then I tried this for the graphics card 
[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)
I got this message 
"Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package xorg-driver-fglrx"

So I'm sort of clueless now :\

With the sounded I got th same error, saved for ncurses-dev gettext rather than the other one, when trying to do the stuff in this thread.  
[http://ubuntuforums.org/showthread.php?t=568463](http://ubuntuforums.org/showthread.php?t=568463)

:(

Any help for this noob would be loved. 

And while I haven't tried to do much with the wireless it shows that the restricted drivers are loaded but it doesn't work. :\

---

### Post by fissionmailed on 2008-01-07
Update: I reinstalled Ubuntu with it connected to the internet.  It's running a lot smoother it seems although it still seems a lack of sound etc but it downloaded the stuff for the videocard with the restricted drivers program.  So that's taken care of it seems.

update2: once I reinstalled it with the internet working(aka cable)  it seems the OS can reach the internet rather that just programs like FF.  I followed that steps in the thread abotu the sound but I still get errors, Using Sound Juicer when I try to play a CD these error come up.

"Error playing CD.
Reason: Could not open resource for writing."
and
"Error playing CD.
Reason: Internal GStreamer error: state change failed. Please file a bug at http://bugzilla.gnome.org/enter_bug.cgi?product=GStreamer."
that comes after I click the close on the second one.

update3: after furiously battling with my computer I got the sound to work.  Other than almost soiling my pants all is fine,  Hopefully the wireless should be easy and if it completely flops I have a Netgear card I know that works that I use in my other laptop. 

Now to load flash and all. w00t w00t

---

### Post by devron6 on 2008-02-29
Hey were you ever able to get your wireless card working? I am having issues. It sees the drivers but I get some kind of config error and cannot activate the wireless.

Thanks

---

### Post by fissionmailed on 2008-03-02
> **devron6 said:**
> Hey were you ever able to get your wireless card working? I am having issues. It sees the drivers but I get some kind of config error and cannot activate the wireless.

Thanks


Yes I was!!

This is what I had to do.  

1. Install ndiswrapper 1.44 or 1.45rc1
2. Edit /etc/network/interfaces and add "ifconfig wlan0 hw ether 00:1b:9e:85:6a:38" in there after the other wlan0 stuff.  Of course your MAC address for your wireless might be different. 
3.  Connect to the internet via command line. Wicd might work but I just use the command line.

I need to do a how to for my satellite.  If you have any questions, feel free to PM me.

---

