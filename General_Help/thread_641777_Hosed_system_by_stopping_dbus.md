---
title: "Hosed system by stopping dbus"
date: 2007-12-15
forum: General Help
---

### Post by eapache on 2007-12-15
I'm running Xubuntu Gutsy on a very old computer, and was browsing the services in order to trim it down a little, when I accidentally disabled dbus. (as an aside, shouldn't it be protected in the same way that gdm and avahi-daemon are?)

Turning it off caused services-admin to close (dbus handles sudo?), so after fiddling around in recovery mode for a bit, I realized I could start it from the cli. I rebooted back into normal mode, started it from the cli, and opened services-admin again. Things looked back to normal, so I checked dbus under services-admin, and rebooted. 

This is where things get wierd. Upon reboot, dbus started normally, but hal, gdm, avahi-daemon, and several other rather important services did not. I started them all manually, and made sure they were all checked under services-admin. I checked my boot messages, and found that it failed to start dhcdbd...?

I'm in way over my head. Something somewhere is really messed up.

---

### Post by astromech on 2007-12-16
I don't know what to do either .Can you boot into a desktop environment if yes  try to put your files in a flash drive then reinstall. Or use a live disc that will give you access to the files on your drive then transfer your files. Sorry I couldn't be more help. Good luck ! Did you try the IRC channels?

:confused:

---

### Post by eapache on 2007-12-16
I have a separate home partition, so worst comes to worst I'll reinstall, but I'd rather not.

After several reboots, things have stabilized a little. I boot normally, have auto-login set, so I get to the xfce desktop, but then I have to launch a terminal and run the following before my system becomes fully functional:
```

sudo /etc/init.d/dhcdbd start
sudo /etc/init.d/hal start
sudo /etc/init.d/avahi-daemon start
sudo /etc/init.d/networking start
sudo /etc/init.d/gdm start
```
Dbus is now starting correctly, but dhcdbd (which is somehow related?) is not. How do I reenable dhcdbd permanently, since it does not show up in services-admin?

---

### Post by eapache on 2007-12-16
I went into the advanced properties of all the services I need turned on and found that on the last run-level they were being stopped. I set them to 'ignore' there instead, and now I only need to start hal and dhcdbd every boot.

Neither of them show up in services-admin, so where do I control them?

And where are the boot logs stored? ctrl-alt-f1 loads the last screens worth, but the message about hal failing is fairly complex and is no longer displayed there. Perhaps some details in that message might help.

---

### Post by astromech on 2007-12-16
I think you know a lot more about this type of thing than me but maybe this will help you enable the boot logs and maybe there you will find the errors :


[http://ubuntuforums.org/showthread.php?t=49925](http://ubuntuforums.org/showthread.php?t=49925)

---

### Post by eapache on 2007-12-16
I couldn't get the system logs to work, so I ended up just reinstalling. Thanks for your help, astromech.

---

### Post by chrisacer on 2008-01-05
I just did the same thing - deselect the 'dbus' service from the list and you are screwed...

BUT you dont need to reinstall - restart the dbus manually using:
```

sudo /etc/init.d/dbus restart
```

and you are back in business!!!

Oh, and remember to go back to the System > Services settings and turn dbus back on there.
:)

---

### Post by chrisacer on 2008-01-07
ahhh - but restarting dbus didnt help things after a reboot - I kept getting a "cant initialise HAL" and none of my hard drives or USB sticks showed up in Xfce on the desktop.

more searching revealed further commands to re-activate dbus for every startup, and that seems to have done the trick:
```

sudo update-rc.d -f dbus remove

sudo update-rc.d dbus defaults 12
```

---

