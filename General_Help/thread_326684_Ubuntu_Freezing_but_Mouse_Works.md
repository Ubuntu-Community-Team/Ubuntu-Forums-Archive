---
title: "Ubuntu Freezing but Mouse Works"
date: 2006-12-28
forum: General Help
---

### Post by jjiknom on 2006-12-28
Hi I just started using Ubuntu 6.10 a week ago.  Its been working great until today.  I heard there was a new Beryl update yesterday.  Then today, Ubuntu notified me of updates and I installed them.  I notcied most of them were beryl updates.  Then I was using it fine until I decided to restart.  Now after I log in, everything freezes except my mouse.  I've looked around for a solution but I can not find anything.  Can someone help?  Thanks!

---

### Post by Bider on 2006-12-28
Can you get any access to a terminal?, Also try logging in by changing the session type.

---

### Post by jjiknom on 2006-12-28
I cant access anything.  Anytime I click the mouse once it freezes everything but the mouse.  I tried loading it in other session types and its the exact same problem.  I'm willing to reinstall ubuntu but I don't want to lose all my files/documents.  I dont know of a way to do that.  

When I do load it in the gnome/safemode I get this msg:

There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Unable to determine the address of the message bus (try 'man dbus-launch' and 'man dbus-daemon' for help)

GNOME will still try to restart the Settings Daemon next time you log in.

---

### Post by Bider on 2006-12-28
Press alt-f2, And a menu will show. Push the down key and locate the  terminal then press enter.
Once the terminal is open, Try the following to remove beryl.

This is only the case if beryl caused the problem.

>  

 // Not sure if this is the keyword for the installation as i dont have beryl installed, But you could try it
sudo apt-get remove beryl.



Then reboot if you cant access the topright corner through keyboard by typing.

> 

// or try simply restarting GDM, by holding ctrl-alt and pushing Backspace.
sudo reboot



If GDM doesnt start at startup type.

> 

sudo gdm start



Also you can reconfigure your xserver by typing.

> 

sudo dpkg-reconfigure xserver**-**xorg



And that should be all. Sorry for the sloppy code, im new to the ubuntu world aswell and linux in general.

---

