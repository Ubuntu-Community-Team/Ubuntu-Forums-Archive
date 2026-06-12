---
title: "Run script/executable before logon"
date: 2007-01-24
forum: General Help
---

### Post by earlsven on 2007-01-24
Hi,

I'm a bit new to linux so need some help, I am using a pc with Ubuntu 6.10 (Gnome) installed on it, but it isn't normally attached to a monitor so I intend to use VNC with it. I have installed the x11vnc package and got it all working fine. I have written a script which when executed loads up the vnc server with the configuration I want, but I am unsure how to set the script to run on boot up, but before any user has logged into the pc. I have tried a few options but the only methods I have thus far been able to try have only succeeded in executing the script after login.

Any suggestions/thoughts greatly appreciated! Please be very clear about the details as I am not familiar with many of the commands etc in linux yet!

Thanks!

---

### Post by matthewstory on 2007-01-24
You'll need to tweak the script a bit, but this is easy enough.  What you want to do is add all the options to the script that you normally get in the init.d . . . e.g. start, stop, restart etc.  Then place the script in the /etc/init.d folder and run the update-rc.d on it:

update-rc.d script.sh defaults

This will load the script into update-rc.d, and so it will start on start up, stop on shutdown etc.  As far as tweaking your script to do all this properly, that's a bit long winded for this forum . . . just google for rc.d and you'll find how-tos.  If you're not particularly concerned about it stopping cleanly, you can just put your script in as is and run that command, and it will just run the script on system start up, and not know what to do on shutdown, which will cause some excess chatter in the syslog, but doesn't do any real harm.

---

### Post by matthewstory on 2007-01-24
my bad, been using debian too much.  You will obviously need to use sudo for the update-rc.d command.

---

### Post by earlsven on 2007-01-24
Thanks, will give this a try shortly :)

---

### Post by earlsven on 2007-01-25
I tried unsuccessfully to make this work for a bit, however on further reading of the documentation for the VNC server I am using I found this

[http://www.karlrunge.com/x11vnc/#faq-display-manager](http://www.karlrunge.com/x11vnc/#faq-display-manager)

Told me exactly how to make that server work before logon. :D Anyone else who has a need for this type of setup this is a good program to use, the VNC server works with minimal configuration unlike some, and appears to have plenty of options if you want extras like encryption :D

---

