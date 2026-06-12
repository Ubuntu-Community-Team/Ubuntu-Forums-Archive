---
title: "problem with mouse and top bar"
date: 2023-10-21
forum: General Help
---

### Post by jgw on 2023-10-21
My mouse will no longer works on my top bar.  I don't think its my mouse but my top bar.  I have included a picture of my top bar.  It also does the same thing with my dash.  It also does the same thing with the top of the Ubuntu forum so I cannot send the picture of my top bar.  

I just re-booted - didn't change anything.  Then I turned on firefox.  Firefox, this screen, etc. ALL block the dash (its on the bottom of the screen.

I also edited this after I re-booted.  I can now run my dash (dash to dock extension)  Top bar still not working It has the following in it:
applications, places, firefox web browser  weather, temp, time and date, shutdown button. clipboard, etc.

If dash is set to get out of the way then the dash is no longer working.  Don't get out of the way and it does work!

tried to run settings and:
sudo gnome-control-center
[sudo] password for greg: 

(gnome-control-center:17394): dconf-WARNING **: 11:37:23.236: failed to commit changes to dconf: Failed to execute child process &#8220;dbus-launch&#8221; (No such file or directory)
Error creating rfkill proxy: (null)
Segmentation fault

But it did turn on settings anyway!!


Seems to work on some things and not others (worked on the posting or this wouldn't be here)

This may have something to do with all of this.  Yesterday I cleverly changed my system display which was now bigger than my monitor (tv).  This means that I couldn't show system settings, etc. to fix the problem.  I then ran sudo gnome-control-center to display settings but it came on and then went away in about 2 seconds.  I then just started trying everything I could think of to get settings to appear so I could fix my mess.  Suddenly it came on long enough for me to reset my display which is where I am now.  Now have access to system settings with no problem.   My fear is that I really screwed something else up.

Oh, one of the things I did was to install unity-control-center display (thought it might work - it didn't)  I can delete it if you want. 

system-info:  [https://paste.ubuntu.com/p/hdMy7fxF88/](https://paste.ubuntu.com/p/hdMy7fxF88/)


Thoughts?

---

### Post by jgw on 2023-10-22
I removed unity-control-center and also nvidia driver and have my top bar back.

---

