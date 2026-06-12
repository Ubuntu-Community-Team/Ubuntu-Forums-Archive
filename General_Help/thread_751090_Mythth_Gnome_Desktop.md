---
title: "Mythth Gnome Desktop"
date: 2008-04-10
forum: General Help
---

### Post by kempy1000 on 2008-04-10
Hello,
I have tried to get mythtv to run at boot using this guide:

Log in Automatically

To log in automatically on startup, change your /etc/gdm/gdm.conf-custom file:

[daemon]
AutomaticLoginEnable=true
AutomaticLogin=mythtv

Run MythTV Frontend Automatically

mythfrontend can be run automatically by adding it to your .gnomerc file. If this file exists in your home directory, it is run on login. Create the file:

gedit /home/mythtv/.gnomerc

Add the following lines:

sleep 10 && mythfrontend > /tmp/mythfrontend.log 2>&1 &

Save the script and make it executable:

chmod 755 .gnomerc


However when i boot my ubuntu now it has a very long delay then suddenly mythtv frontend appears with the gnome desktop over the top of it, as if mythtv frontend is the desktop background.

If anyone has a better method to get mythtv to start at boot without the overhead of a gnome session please say because this is my least prefared method but after scouring the internet I had no other option. 
If not maybe just a fix for my current setup?

Thanks
Chris

---

### Post by Scorpuk on 2008-04-10
I get mythfrontend to run automatically and didnt create any scripts.


There should be an option somewhere, not at my linux machine now, to log a user on after xxx seconds.

After that you can goto sessions, I think, and add mythfrontend to programs to run at start-up.


This is on ubuntu 7.1 btw.

---

### Post by kempy1000 on 2008-04-10
Thanks,
I removed them scripts and used gnome to auto login mythtv
and then sessions to run mythfrontend

But I get exact same problem, I have attached a screen shot just incase.

Thanks
Chris

---

### Post by kempy1000 on 2008-04-10
Ok so following this guide proved very useful!
[http://prettymad.net/articles/how_to_build_a_myth_tv_box2](http://prettymad.net/articles/how_to_build_a_myth_tv_box2)

My box works now.

However it still boots a full gnome session before running mythv can this be stopped?

Thanks 
Chris

---

