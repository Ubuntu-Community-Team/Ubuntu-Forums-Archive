---
title: "unable to login since KDM theme install"
date: 2008-02-17
forum: General Help
---

### Post by Mooneater on 2008-02-17
Just today I installed a new theme for KDM manager, which should pimp my login-screen, found at: [link](http://www.kde-look.org/content/show.php/Krystal?content=22390).

However, after rebooting, I get an error message stating something like:

corrupt theme, can not find entry for username/password fields, will use default themer now.

Well, allright, clicked that through.

However, after that I get a standard GNOME inlog screen, but with the username and password fields disabled. I think the best way to fix this should be restarting in recovery mode and change the inlogscreen theme thingy through the console... but I have no clue howto :)

The linux distro on my pc is Dapper Drake (actually I was just about to update it all the way to Gutsy..)

But right now I can't do anything :(

Tnx in advance :)

---

### Post by Mooneater on 2008-02-17
Ok, I figured it out from some other topic around here... I should've written down the error msg

the error msg is: " the greeter theme is corrupt".

To fix this:

1. hit alt + ctrl + f2 at your (not working) inlog screen, this will take you to terminal mode
2. type: sudo killall kdm
3. type: sudo remove kdm
4. type: sudo apt-get install kdm

this should first remove your kdm, and after that install a fresh one. Only drawback is that you seem to loose quite some settings (applets activated, backgrouds chosen etc)


If you happen to want to visit the graphical userinterface inbetween, you can always do:
sudo killall kdm
and: startx

---

