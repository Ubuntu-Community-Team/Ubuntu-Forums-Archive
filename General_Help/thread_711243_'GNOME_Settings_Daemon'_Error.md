---
title: "'GNOME Settings Daemon' Error"
date: 2008-02-29
forum: General Help
---

### Post by stuartwood89 on 2008-02-29
> There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.

This comes up when I log in from time to time.  It's really annoying because my theme doesn't load and everything goes back to the normal Ubuntu theme.  I usually have to log off and log back on again and it'll be fine, but I really don't want to go through that all the time.

Can anyone tell me what this means and help me to stop it from happening?

Thanks.

Stu

PS: I know there are other threads with the same problem, but none of them have answers, that's why I'm posting this.

---

### Post by stooshbunutu on 2008-02-29
This is a random error that happens from time to time:

If it happens and you don't want to reboot, you can start it manually

press Alt+F2 to open a run dialog, then type: ```
gnome-settings-daemon
```and then click on run. A few seconds later things should be back to normal.

Hope this helps :)

---

### Post by Nythain on 2008-02-29
so im assuming that, given teh number of actual unanswered posts concerning this problem, there's no actual fix for this... its just a "sucks to be you, live with it" situation at the moment???

---

### Post by stuartwood89 on 2008-03-01
> so im assuming that, given teh number of actual unanswered posts concerning this problem, there's no actual fix for this... its just a "sucks to be you, live with it" situation at the moment???

Looks like it lol.

stooshbuntu:  I'll give that a try when I'm next on Ubuntu and let you know the outcome.

Thanks for the replies :)

---

### Post by brownknight on 2008-03-03
I have experienced the same problem. I think it has to do with the last update I did yesterday (sudo aptitude update && sudo aptitude upgrade). I will try to find out what the last packages were updated (I am still a noob). 

I got this error:
[I][B]There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.

[/B][/I]
Next, I did right-click and change desktop background and I got this error:

[I][B]Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager.
[/B][/I]


I then manually started the daemon by opening up a terminal and typing in: gnome-settings-daemon

This worked and started the theme but it left this error in the terminal:
[B][I]** (gnome-settings-daemon:6069): WARNING **: Unable to connect to dbus: Failed to connect to socket /tmp/dbus-VECLoGmS1o: Connection refused

(gnome-settings-daemon:6069): GnomeKbdIndicator-WARNING **: Unable to connect to dbus: Failed to connect to socket /tmp/dbus-VECLoGmS1o: Connection refused

(gnome-settings-daemon:6069): GnomeKbdIndicator-WARNING **: Not connected to dbus, will not register the object
xrdb:  "*Label.background" on line 220 overrides entry on line 150
xrdb:  "*Text.background" on line 226 overrides entry on line 191
xrdb:  "*Label.foreground" on line 232 overrides entry on line 151
xrdb:  "*Text.foreground" on line 238 overrides entry on line 192

** (gnome-screensaver:6078): WARNING **: failed to register with the message bus




[/I][/B]

How do I go about reporting this in launchpad?

---

### Post by brownknight on 2008-03-15
Since the release of Alpha 6, I have not encountered this error anymore. Looks like already fixed? How about you guys?

---

### Post by Peter09 on 2008-03-15
I am still seeing this error.

PC

---

### Post by spliner on 2008-03-25
I'm seeing this error on several of my Ubuntu 7.10 systems as well.  It's very random, and usually logging out and then in again seems to fix the issue.  It's annoying but I love Gnome+Ubuntu too much to give up on it.  I'm hoping there is a future fix for it though.

-Spliner

---

